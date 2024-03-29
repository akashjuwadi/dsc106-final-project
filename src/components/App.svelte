<main>
  <!-- svelte-ignore a11y-missing-attribute -->
  <html>
    <script src="https://d3js.org/d3.v7.min.js"></script>
    <head>
      <title>DSC 106 Final Group Project</title>
    </head>
    <body style="background-color:#DDE6ED">
    <div class="div-1">
        <h1>Measuring Economic Health</h1>
        <h2 style="padding:0px">Gross Domestic Product per Capita and the Gini Coefficient</h2>
          <p>
            As data scientists, we apply our domain knowledge to pinpoint relevant data sources, ensuring alignment with the intended message. 
            This expertise guides our selection process, leading to more accurate and impactful insights. 
            By leveraging both domain understanding and data exploration techniques, we can effectively communicate findings that resonate with our audience.
            Let's see how this idea applies in the case of explaining the strength of a country's economy!</p>
    </div>
    <div class="div-2">
        
          <h3>Gross Domestic Product (GDP)</h3>
          <p>There are many factors which lend to the strength of a country's economy, such as:</p>
          <ul>
            <li>Trade (imports and exports)</li>
            <li>Labor force participation (employed, unemployed, and not in the labor force)</li>
            <li>Income</li>
          </ul>
          <p>GDP tends to be the most popular statistic for indicating a nation's 
            wealth because it measures the monetary value of final goods and services. That is, it measures the sum of all 
            consumption, investment, government purchases, and net exports (exports minus imports) over a given period of time.

            
            Explore how GDP differs across countries in the below visualization.
          
          </p>
      
      
        <h3>GDP Per Capita Globally</h3>
        <div id="gdp_choropleth" align="center">
          <span id="mapYear" style="font-size:14px" align="right">Year: 1960</span>
            <script src="https://cdnjs.cloudflare.com/ajax/libs/d3-legend/2.25.6/d3-legend.min.js"></script>
            <br>
        </div>
    </div>

    <div class="div-3">
        <h3>Why could GDP possibly be flawed?</h3>
        <p>GDP doesn't give a full picture of how economic prosperity is distributed because:</p>
        <ul>
          <li>Large countries may have greater GDPs simply because they have a large population. GDP per capita can help with this.</li>
          <li>A high GDP per capita doesn't mean that all of the nation's people are benefitting equally, depending on how wealth is distributed across the population.</li>
        </ul>
        <h3>The Gini Index</h3>
        <p>Economic inequality within a nation can be indicated with the Gini Coefficient, 
          a metric derived from the Lorenz curve. The Lorenz Curve is a graph of the population's income distribution. 
          The graph has the percent of the population on the x-axis and the percent of overall income earned on the y-axis. 
          A line starting from the origin and angled at 45 degrees represents perfect equality. Along this line, any x percent of the population earns exactly x percent of the total income. 
          The area between the Lorenz curve and the 45 degree line is the Gini Coefficient. A greater Gini Coefficient indicates greater inequality.</p>
  
      <div id="lorenzCurve" align="center"><input type="range" name="range" class="slider" id="giniSlider" value="0.1"
        min="0.1" max="0.5" step="0.1">
        <span id="giniVal" style="font-size:14px" align="center">Gini Coefficient: 0.1</span>
        <div id="lorenzInfo">The poorest 50% of the population owns 42% of the wealth.</div>
          <br>
        </div>
        <br>
        <br>
    </div>
  

    <div class="div-4">
    

      <div>
        <h3>Do these two metrics always agree for each country?</h3>
        <label for="yearSelect">Select Year to Compare:</label>
        <select id="yearSelect">   
          <option value="1985" selected>1985</option>
          <option value="1986">1986</option>
          <option value="1987">1987</option>
          <option value="1988">1988</option>
          <option value="1989">1989</option>
          <option value="1990">1990</option>
          <option value="1991">1991</option>
          <option value="1992">1992</option>
          <option value="1993">1993</option>
          <option value="1994">1994</option>
          <option value="1995">1995</option>
          <option value="1996">1996</option>
          <option value="1997">1997</option>
          <option value="1998">1998</option>
          <option value="1999">1999</option>
          <option value="2000">2000</option>
          <option value="2001">2001</option>
          <option value="2002">2002</option>
          <option value="2003">2003</option>
          <option value="2004">2004</option>
          <option value="2005">2005</option>
          <option value="2006">2006</option>
          <option value="2007">2007</option>
          <option value="2008">2008</option>
          <option value="2009">2009</option>
          <option value="2010">2010</option>
          <option value="2011">2011</option>
          <option value="2012">2012</option>
          <option value="2013">2013</option>
          <option value="2014">2014</option>
          <option value="2015">2015</option>
          <option value="2016">2016</option>
          <option value="2017">2017</option>
          <option value="2018">2018</option>
          <option value="2019">2019</option>
          <option value="2020">2020</option>
        </select>
      </div>
      <div class='center'>
        <svg id="scatterplot" width="400" height="300"></svg>

      <br>
      <br>
 
      <div>
        <h3>Notice how weak the correlation between the two metrics is throughout the years?</h3>
        <p>In 2020, the United States had a higher GDP per Capita than 27 of 29 European nations, yet had a worse Gini index than all but one of them. How can that be?</p>
        
        <p>If only one metric was satisfactory for measuring an economy's health, the correlation between the two would be nearly perfect beause they would always "agree" on the relative health of the economy. However, it can be seen that this is not the case. 
          It is fairly common for a country to have a more impressive GDP per Capita (a greater value along the y-axis) but have a less impressive Gini Coefficient (a greater value along the x-axis).</p> 
      </div>
    </div>
      <br>
      <br>
      <br>

    <div class="div-5">
      <div>
        <h3>What have we learned?</h3>
        <ul>
          <li>GDP measures economic activity well, but fails to provide information on what proportion of the population is involved in said activity.</li>
          <li>The Gini index describes wealth distribution well, but does not indicate the level of either cumulative or average wealth.</li>
          <li>A more complete picture is obtained by considering both metrics, and taking into account each of their strengths and weaknesses.</li>
        </ul>
        <p>This economics example shows how important domain knowledge is in developing effective data visualizations. 
          Now we know what information GDP can provide, and what information is better conveyed with the Gini Coefficient. 
          This applies to a wide variety of subjects! Next time you're making a visualization, consider: is this the best metric for my story?</p>
      </div>

      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
  
    

      <div class="center">
        <iframe width="800" height="600" src="https://www.youtube.com/embed/Fv5OA3sOYcE"></iframe>
      </div>
    </div>
  </body>
    </html>
</main>

<script>
  import * as d3 from 'd3';
  import { onMount } from 'svelte';
  import { scaleLinear } from 'd3-scale';
  // import Legend from "./Legend-GDP.svelte";
  // import {
  //   format,
  //   groups,
  //   interpolatePiYG,
  //   pairs,
  //   quantile,
  //   range,
  //   scaleSequential,
  // } from "d3";

  // const color = scaleSequential(d3.interpolateBlues).domain(d3.extent(gdpData, function(d){return d.gdp;}));

  const width = 928;
  const height = 500;
  const marginTop = 10;
  const marginRight = 10;
  const marginBottom = 20;
  const marginLeft = 40;

  let data = [];

  onMount(async () => {
      const res = await fetch(
          'gdp_gini.csv',
      );
      const csv = await res.text();
      data = d3.csvParse(csv, function(d){
          return{
             year: +d["year"],
             country: d["country"],
             country_code: d["country_code"],
             gdp: +d["gdp"],
             gini: +d["gini"]/100,
             region: d["region"],
          };
      });
    drawScatter(data);
    document.getElementById('yearSelect').addEventListener('change', function() {
      drawScatter(data);
    });
    
    drawGDP(data);
    
  });

  let lorenzData = [];

onMount(async () => {

 const res = await fetch('lorenz_simulation.csv'); 

 const csv = await res.text();

 lorenzData = d3.csvParse(csv, function(d){
    return{
        gini: +d.gini,
        pop: +d.population,
        income: +d.income
    };
 })

 drawLorenz(lorenzData);


});


function drawLorenz(lorenzData){
var margin = {top: 30, right: 30, bottom: 45, left: 60},
width = 560 - margin.left - margin.right,
height = 500 - margin.top - margin.bottom;

var svg = d3.select("#lorenzCurve")
.append("svg")
.attr("width", width + margin.left + margin.right)
.attr("height", height + margin.top + margin.bottom)
.append("g")
.attr("transform",
      "translate(" + margin.left + "," + margin.top + ")")
      

// x and y scales
var x = d3.scaleLinear()
  .domain(d3.extent(lorenzData, function(d){return d.pop;}))
  .range([ 0, width ]);

svg.append("g")
  .attr("transform", "translate(0," + height + ")")
  .call(d3.axisBottom().scale(x).tickFormat(d3.format(".0%")));

var y = d3.scaleLinear()
  .domain(d3.extent(lorenzData, function(d){return d.income;}))
  .range([ height, 0]);

svg.append("g")
  .call(d3.axisLeft().scale(y).tickFormat(d3.format(".0%")));


// 45 degree line
svg.append('line')
    .style("stroke", "#CF541F")
    .style("stroke-dasharray", ("3, 3"))
    .style("stroke-width", 4)
    .attr("x1", width)
    .attr("y1", 0)
    .attr("x2", 0)
    .attr("y2", height);


// original lorenz curve at gini = 0.1
var gini = 0.1;


function filterData(data, giniValue){
    return data.filter(function(entry){
        return entry.gini===giniValue;
    });
};


// initialize line
var line = svg.append('g')
    .append("path")
        .datum(filterData(lorenzData, gini))
        .attr("d", d3.line()
            .x(function(d) { return x(d.pop)})
            .y(function(d) { return y(d.income)})
            )
        .attr("stroke", function(d){return "darkblue"})
        .style("stroke-width", 3)
        .style("fill", "#A2D7D4")
        


function update(gini){
    // new data
    var filteredLorenz = filterData(lorenzData, gini)

    line.datum(filteredLorenz)
        .transition()
        .duration(1000)
        .attr("d", d3.line()
            .x(function(d){return x(d.pop)})
            .y(function(d){return y(d.income)})
        )
        .attr("stroke", function(d){return "darkblue"})
        
};


// slider updates gini value and draws new lorenz curve
d3.select("#giniSlider").on("input", function(){
    gini = Number(this.value);
    update(gini);
    var wealth = Math.round(filterData(lorenzData, gini)[5]['income'] * 100);
    document.getElementById("giniVal").textContent=`Gini Coefficient: ${gini}`;
    document.getElementById("lorenzInfo").textContent=`The poorest 50% of the population owns ${wealth}% of the wealth.`
});


// axis labels 
svg.append("text")
    .attr("class", "x label")
    .attr("text-anchor", "end")
    .attr("x", width)
    .attr("font-size", 14)
    .attr("y", height+40)
    .text("Percent of Population");

svg.append("text")
    .attr("class", "y label")
    .attr("text-anchor", "end")
    .attr("y", -50)
    .attr("dy", ".75em")
    .attr("font-size", 14)
    .attr("transform", "rotate(-90)")
    .text("Percent of Income");

//chart title 
svg.append("text")
    .attr("x", (width / 2))             
    .attr("y", 0 - (margin.top / 2))
    .attr("text-anchor", "middle")  
    .style("font-size", "14px") 
    .style("text-decoration", "underline")  
    .text("Lorenz Curve");

// shading?
// tooltip to show 

};



// Define the Scatter component as a Svelte function
function drawScatter(filteredData) {
      const initialYear = document.getElementById('yearSelect').value
      let yearAsInteger = parseInt(initialYear);
      filteredData = filteredData.filter(d => d.year === yearAsInteger);
      filteredData = filteredData.filter(d => d.gdp !== 0);   
      filteredData = filteredData.filter(d => d.gini !== 0);    
      d3.select("#scatterplot").selectAll("*").remove();
    // Define the SVG dimensions and margins
      const margin = { top: 50, right: 100, bottom: 50, left: 110 };
      const width = 1000 - margin.left - margin.right;
      const height = 600 - margin.top - margin.bottom;

    // Append SVG container to the body
      const svg = d3.select("#scatterplot")
          .attr("width", width + margin.left + margin.right)
          .attr("height", height + margin.top + margin.bottom)
          .append("g")
          .attr("transform", `translate(${margin.left},${margin.top})`);

    // Define scale for x
      var xScale = scaleLinear()
          .domain(d3.extent(filteredData, function(d){return d.gini}))
          .range([0, width]);
      var xAxis = d3.axisBottom()
            .scale(xScale)
    // Add x-axis
      svg.append("g")
          .attr("transform", `translate(0,${height})`)
          .call(xAxis);
    // x grid 
      svg.append("g")
      .attr("class", "grid")
      .attr("transform", `translate(0,${height})`)
      .call(xAxis.tickSize(-height).tickFormat(""))
      .selectAll("line").style("stroke", "#9DB2BF");
      
    // define scale for y
      var yScale = scaleLinear()
          .domain(d3.extent(filteredData, function(d){return d.gdp}))
          .range([height, 0]);
      var yAxis = d3.axisLeft()
          .scale(yScale)
          .tickFormat(d => `$${d3.format(",")(d)}`);
    // Add y-axis
      svg.append("g")
        .call(yAxis);
    // y grid
      svg.append("g")		
        .attr("class", "grid")
        .call(yAxis.tickSize(-width).tickFormat(""))
        .selectAll('line').style("stroke", "#9DB2BF");
    
  

    // Plot points with tooltip
      const colorScale = d3.scaleOrdinal()
      .domain(["NA", "SA", "OC", "AF", "AS", "EU"]) // Continent codes
      .range(["#1f77b4", "#ff7f0e", "#2ca02c", "#d62728", "#9467bd", "#8c564b"]); // Colors for continents
      


      svg.append("g")
          .selectAll("dot")
          .data(filteredData)
          .enter()
          .append("circle")
          .attr("cx", function(d){ return xScale(d.gini);})
          .attr("cy", function(d){ return yScale(d.gdp);})
          .attr("r", 7) // radius of the circles
          .style("fill", function(d) { return colorScale(d.region); })
          .append("title")
          .text(d => `Country: ${d.country}
          \nGDP: $${d3.format(",.2f")(d.gdp)}
          \nGini: ${d3.format(",.3f")(d.gini)}`);
    
    
      // Add axis labels
    svg.append("text")
      .attr("text-anchor", "middle")
      .attr('x', width/2)
      .attr('y', margin.top+500)
      // .attr("transform", `translate(${width / 2},${height + margin.top + 10})`)
      .text("Gini Index");

      svg.append("text")
          .attr("text-anchor", "middle")
          .attr("transform", `translate(${-margin.left + 10},${height / 2})rotate(-90)`)
          .text("GDP Per Capita (current US$)");
      svg.append("text")
        .attr("x", width / 2)
        .attr("y", margin.top-80)
        .attr("text-anchor", "middle")
        .style("font-size", "1.5em")
        .text("GDP vs. Gini");

    // Adding Legend
    svg.append('rect')
      .attr("width", 130)
      .attr("height", 150)
      .attr("x", width-margin.right-32)
      .attr("y", margin.top-10)
      .attr("fill", "#DDE6ED")
      .attr("fill-opacity", "0.7")
    const legend = svg.append("g")
        .attr("class", "legend")
        .attr("transform", `translate(${width - margin.right - 15},${margin.top+ 20})`)
        

    const continents = ["North America", "South America", "Oceania", "Africa", "Asia", "Europe"]; 

    legend.selectAll("rect")
        .data(continents)
        .enter()
        .append("rect")
        .attr("y", function(d, i) { return i * 20; })
        .attr("width", 10)
        .attr("height", 10)
        .style("fill", function(d, i) { return colorScale(["NA", "SA", "OC", "AF", "AS", "EU"][i]); });

    legend.selectAll("text")
        .data(continents)
        .enter()
        .append("text")
        .attr("x", 15)
        .attr("y", function(d, i) { return i * 20 + 9; })
        .text(function(d) { return d; });
    
    legend.append("text")
        .attr("x", 0)
        .attr("y", -10)
        .text("Regions")
        .style("font-weight", "bold");
  };


// define GDP choropleth as a Svelte Function
const drawGDP = async (data) => {
  // dimensions
  const width = 800
  const height = 700;
  var margin = {top: 0, right: 30, bottom: 45, left: 60};

  // Append SVG 
  const svg = d3.select('#gdp_choropleth').append('svg') 
      .attr('width', width)
      .attr('height', height);


  // Define projection
  const projection = d3.geoMercator()
      .scale(130)
      .translate([width / 2, height / 1.5]);

  // Define path generator
  const path = d3.geoPath().projection(projection);

  const formatGDP = (code, d) => {
      if (d.find(entry=>entry.country_code===code)==null){
        return "No Data"
      } else {
        return `$${d.find(entry=>entry.country_code===code).gdp.toFixed(2)} USD`
      }
          }

  // Add legend
  const gdpRange = [0, 110000];
    
    // Define color scale
  const colorScale = d3.scaleSequential(['lightblue', 'darkblue']).domain(gdpRange);
  const legendWidth = 15;
  const legendHeight = 150;

  const legend = svg.append("g").attr("transform", "translate(700,20)");

  const legendGradient = legend.append("defs")
        .append("linearGradient")
        .attr("id", "linear-gradient")
        .attr("x1", "0%")
        .attr("y1", "0%")
        .attr("x2", "0%")
        .attr("y2", "100%");
  
  legendGradient.append("stop")
      .attr("offset", "0%")
      .attr("stop-color", colorScale(gdpRange[1]));

  legendGradient.append("stop")
      .attr("offset", "100%")
      .attr("stop-color", colorScale(gdpRange[0]));

  legend.append("rect")
      .attr("width", legendWidth)
      .attr("height", legendHeight)
      .style("fill", "url(#linear-gradient)");

  const legendScale = d3.scaleLinear()
      .domain([gdpRange[0], gdpRange[1]])
      .range([legendHeight, 0]);

    const legendAxis = d3.axisRight(legendScale)
    .tickFormat(d3.format("$,"));

    legend.append("g")
          .attr("transform", `translate(${legendWidth},0)`)
          .call(legendAxis);


  
  try {
      // Load world map data with //
      const world = await d3.json('world-110m.geojson')
      world.features = world.features.filter (function(d) { return d.id !== "ATA"; });
      // Tooltip highlight
      
      const tooltip = d3.select("body").append("div")
        .attr("class", "tooltip")
        .style("opacity", 0);

      let mouseOver = function(d) {
        svg.selectAll("path")
          .transition()
          .duration(200)
          .style("opacity", .5)
          .style("stroke", "transparent");
        d3.select(this)
          .transition()
          .duration(200)
          .style("opacity", 1)
          .style("stroke", "black");
        

      }

      let mouseLeave = function() {
        svg.selectAll("path")
          .transition()
          .duration(200)
          .style("opacity", 1)
          .style("stroke", "transparent");
      }

      // Draw map paths
      svg.selectAll('path')
          .data(world.features)
          .enter().append('path')
          .attr('d', path)
          .attr('fill', d => {
              // Get GDP data for each country
              const countryData = data.find(entry => entry.country_code === d.id);
              return countryData ? getColor(countryData.gdp) : 'gray'; // Color countries based on GDP
          })
          .on("mouseover", mouseOver)
		      .on("mouseleave", mouseLeave)
          .append("title")
          .text(function(d) { 
            const gdpPerCapita = formatGDP(d.id, data);
            return `${d.properties.name} \nGDP Per Capita: ${gdpPerCapita !== '$0.00 USD' ? gdpPerCapita : 'No Data'}`;
	});


      // Add slider
      const slider = d3.select('#gdp_choropleth').append('input')
          .attr('type', 'range')
          .attr('min', d3.min(data, d => d.year))
          .attr('max', d3.max(data, d => d.year))
          .attr('step', 1)
          .style('position', 'absolute')
          .style('right', '780px')
          .on('input', function() {
              // Update map based on selected year
              const selectedYear = +this.value;
              const filteredData = data.filter(d => d.year === selectedYear);

              document.getElementById("mapYear").textContent=`Year: ${selectedYear}`;
              
              svg.selectAll('path')
                  .data(world.features)
                  .attr('fill', d => {
                      const countryData = filteredData.find(entry => entry.country_code === d.id);
                      return countryData ? getColor(countryData.gdp) : 'gray';
                  })
                  .on("mouseover", mouseOver)
		              .on("mouseleave", mouseLeave)
              svg.selectAll('title').text(function(d) { return `${d.properties.name} \nGDP Per Capita: ${formatGDP(d.id, filteredData)}`});
          });

          
        

  } catch (error) {
      console.error('Error loading world map data:', error);
  }

  
  
};

// Function to get color based on GDP value
const getColor = (gdp) => {
    // Define color scale
    const colorScale = d3.scaleLinear()
        .domain([100, 110000]) // Adjust domain based on GDP range
        .range(['lightblue', 'darkblue']);

    // Return color based on GDP value
    return colorScale(gdp);
};

</script>




<style>

    @import
    url("https://fonts.googleapis.com/css2?family=League+Spartan:wght@100..900&display=swap");
    @import
    url("https://fonts.googleapis.com/css2?family=League+Spartan:wght@100..900&family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&display=swap");
  /* Write your CSS here */
    @import url('https://fonts.googleapis.com/css2?family=Nunito:wght@300;400;700&display=swap');

  :root {
    --color-bg: #ffffff;
    --color-outline: #c2c2c2;
    --color-shadow: hsl(0, 0%, 0%, 0.1);
    --color-text: #3f4252;
    --color-bg-1: hsla(0, 0%, 0%, 0.2);
    --color-shadow-1: hsl(0, 0%, 96%);
  }

  /* *,
  *::before,
  *::after {
    margin: 10px;
    padding: 10px;
    box-sizing: border-box;
  } */


    main {
        text-align: left;
        color: #27323F;
        font-family:'Libre Baskerville', serif;
        font-size:12px;
        line-height: 1.5;
        background-color:  #DDE6ED;
        /* padding: 40px; */
    }

    
    h1 {
        font-family:'League Spartan', sans-serif;
        font-size: 60pt;
        margin-bottom: 10px;
        text-align:center;
        line-height: 1;
    }
    h2 {
        font-size: 18pt;
        padding:20px;
        text-align:center;

    }
    h3 {
        font-size: 16pt;
        padding:15px;
        text-align:center;
    }
    p {
        font-size: 12pt;
        padding:15px;
        text-align:left;
    }
    div.center {
      text-align: center;
    }
    ul { 
      list-style-type: none; 
      padding: 0; 
    }
    li {
      text-indent:5px;
      margin:25px;
      text-align:left;
      font-size: 12pt;
    }
    li::before { 
      content: '• '; 
      text-align:left;
    } 
    .div-1 {
      background-color: #BDCCD6 ;
      padding:80px;

    }
    .div-2 {
    	background-color: #DDE6ED;
      padding: 40px;
    }
    .div-3 {
    	background-color: #BDCCD6;
      padding: 40px;
    }
    .div-4 {
      background-color: #DDE6ED;
      padding: 40px;
    }
    .div-5 {
    	background-color: #BDCCD6;
      padding: 40px;
    }
</style>

