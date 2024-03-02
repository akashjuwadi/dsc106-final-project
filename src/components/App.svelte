<script>
  import * as d3 from 'd3';
  import { onMount } from 'svelte';
  import Graph from './Graph.svelte';

  const width = 928;
  const height = 500;
  const marginTop = 10;
  const marginRight = 10;
  const marginBottom = 20;
  const marginLeft = 40;

  let data = [];
  let targetYear = "1964";
  let targetCountryCode = "USA";

  onMount(async () => {
      const res = await fetch(
          '/gdp_gini_filtered_data.csv',
      );
      const csv = await res.text();
      await d3.csvParse(csv, (d) => {
          data.push({
             year: +d["Year"],
             country_name: d["Country Name"],
             country_code: d["Country Code"],
             indicator_code: d["Indicator Code"],
             indicator_name: d["Indicator Name"],
             value: +d["Value"],
          });
      });
      data = data;
  });
  /*
  $: console.log(data)
  let geoJsonData = {}
  let projectionType = d3.geoEquirectangular();
  let geoGenerator = d3.geoPath().projection(projectionType);
  let u = d3.select('#content g.map')
    .selectAll('path')
    .data(geojsonData.features)
    .join('path')
    .attr('d', geoGenerator);

  const ttWidth = 180;
  const ttHeight = 200;
  const ttPaddingTop = 30;
  const ttPaddingLeft = 15;
  const ttLineHeight = 36;

  let mousePosition = [0, 0];
  function recordMousePosition(event) {
    mousePosition = d3.pointer(event);
  }
  const bisect = d3.bisector((d) => d.data[0]).center;
  let selectedArea = null;
  let selectedPoint = null;
  function setSelected(area) {
    selectedArea = area;
    const i = bisect(area, x.invert(mousePosition[0])); // x must be defined
    const [_, groupData] = area[i].data; // still needs to be modified
    selectedPoint = groupData.get(name(area.key)).get(sex(area.key)); // still needs to be modified
  }
  */
</script>

<main>
  <Graph {data}/>
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
/*
  h1 {
    font-size: 2em;
    font-weight: 300;
    line-height: 2;
  }
*/  
</style>