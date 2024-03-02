<script>
    import * as d3 from 'd3'; 
    import { onMount } from 'svelte';
    import { scaleLinear, scaleTime } from 'd3-scale';
    import { select } from 'd3-selection';
    import { timeFormat } from 'd3-time-format';
    export let data;
    let targetYear = 1990;
    let targetCountryCode = "USA";
    console.log(data)
    let filteredData = [];

  onMount(() => {
    // Filter data based on the target year and country code
    filteredData = data.filter(d => d.year === targetYear)// && d.country_code === targetCountryCode);
    console.log(filteredData)
    // Extract Gini index (SI.POV.GINI) and GDP (current US$) (NY.GDP.MKTP.CD) values from filtered data
    const giniValues = filteredData.filter(d => d.indicator_code === "SI.POV.GINI").map(d => d.value);
    const gdpValues = filteredData.filter(d => d.indicator_code === "NY.GDP.MKTP.CD").map(d => d.value);
    
    // Set up the SVG dimensions
    const margin = { top: 20, right: 20, bottom: 50, left: 50 };
    const width = 800 - margin.left - margin.right;
    const height = 600 - margin.top - margin.bottom;

    // Append SVG container to the body
    const svg = select("#scatterplot")
      .attr("width", width + margin.left + margin.right)
      .attr("height", height + margin.top + margin.bottom)
      .append("g")
      .attr("transform", `translate(${margin.left},${margin.top})`);

    // Define scales for x and y axes
    const xScale = scaleLinear()
      .domain([Math.min(...giniValues), Math.max(...giniValues)])
      .range([0, width]);

    const yScale = scaleLinear()
      .domain([Math.min(...gdpValues), Math.max(...gdpValues)])
      .range([height, 0]);

    // Plot points
    svg.selectAll(".dot")
      .data(filteredData)
      .enter().append("circle")
      .attr("class", "dot")
      .attr("cx", d => xScale(d.indicator_code === "SI.POV.GINI" ? d.value : null))
      .attr("cy", d => yScale(d.indicator_code === "NY.GDP.MKTP.CD" ? d.value : null))
      .attr("r", 5); // radius of the circles

    // Add x-axis
    svg.append("g")
      .attr("transform", `translate(0,${height})`)
      .call(d3.axisBottom(xScale));

    // Add y-axis
    svg.append("g")
      .call(d3.axisLeft(yScale));

    // Add axis labels
    svg.append("text")
      .attr("text-anchor", "middle")
      .attr("transform", `translate(${width / 2},${height + margin.top + 10})`)
      .text("Gini Index");

    svg.append("text")
      .attr("text-anchor", "middle")
      .attr("transform", `translate(${-margin.left + 10},${height / 2})rotate(-90)`)
      .text("GDP (current US$)");
  });
</script>

<svg id="scatterplot" width="800" height="600"></svg>