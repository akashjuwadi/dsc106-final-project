<script>
  import { onMount } from 'svelte';
  import * as d3 from 'd3';

  let gdpData = [];

  onMount(async () => {
    const res = await fetch("countries_gdp.csv");
    const csv = await res.text();
    await d3.csvParse(csv, (d) => {
      gdpData.push({
        country: ["Country Name"],
        year: new Date(Date.UTC(d["year"])), //
        gdp: ["country"] //
      });
    });
    gdpData = gdpData;
  });

  // Write your JS here, or import other files
  var svg = d3.select("svg"),
    width = +svg.attr("width"),
    height = +svg.attr("height");
  
  var path = d3.geoPath();
  var projection = d3.geoMercator()
    .scale(70)
    .center([0, 20])
    .translate([width / 2, height / 2]);
  
  var map = d3.map();
  var colorScale = d3.scaleThreshold()
    .domain([100000, 1000000, 10000000, 30000000, 100000000, 500000000])
    .range(d3.schemeBlues[7])
  
  // load json and/or csv data here

  function ready(error, topo) {
    svg.append("g")
      .selectAll("path")
      .data(topo.features)
      .enter()
      .append("path")
        .attr("d", d3.geoPath()
        .projection(projection)
      )
      .attr("fill", function (d) {
        d.total = data.geo(d.id) || 0;
        return colorScale(d.scale);
      });
  }

</script>

<main>
  <h1>Svelte template</h1>

  <p>Write your HTML here</p>
</main>

<style>
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

  *,
  *::before,
  *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  main {
    text-align: center;
    font-family: 'Nunito', sans-serif;
    font-weight: 300;
    line-height: 2;
    font-size: 24px;
    color: var(--color-text);
  }

  h1 {
    font-size: 2em;
    font-weight: 300;
    line-height: 2;
  }
</style>
