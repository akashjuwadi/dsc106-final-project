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

 console.log(lorenzData);

 drawLorenz(lorenzData);


});


function drawLorenz(lorenzData){
var margin = {top: 30, right: 30, bottom: 60, left: 60},
width = 460 - margin.left - margin.right,
height = 400 - margin.top - margin.bottom;

var svg = d3.select("#lorenzCurve")
.append("svg")
.attr("width", width + margin.left + margin.right)
.attr("height", height + margin.top + margin.bottom)
.append("g")
.attr("transform",
      "translate(" + margin.left + "," + margin.top + ")");

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
    .style("stroke", "darkgreen")
    .style("stroke-dasharray", ("3, 3"))
    .style("stroke-width", 3)
    .attr("x1", width)
    .attr("y1", 0)
    .attr("x2", 0)
    .attr("y2", height);


// original lorenz curve at gini = 0.1
var gini = 0.1;
//var filteredLorenz = filterData(lorenzData, gini);

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
        .style("fill", "none")



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
    document.getElementById("giniVal").textContent=`Gini Coefficient: ${gini}`;
});

// axis lables 
svg.append("text")
    .attr("class", "x label")
    .attr("text-anchor", "end")
    .attr("x", width)
    .attr("y", height+40)
    .text("Percent of Population");

svg.append("text")
    .attr("class", "y label")
    .attr("text-anchor", "end")
    .attr("y", -50)
    .attr("dy", ".75em")
    .attr("transform", "rotate(-90)")
    .text("Percent of Income");

//chart title 
svg.append("text")
    .attr("x", (width / 2))             
    .attr("y", 0 - (margin.top / 2))
    .attr("text-anchor", "middle")  
    .style("font-size", "16px") 
    .style("text-decoration", "underline")  
    .text("Lorenz Curve and Gini Coefficient");

// shading?
// tooltip to show what percent of population has what percent of income

};




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
  <!-- svelte-ignore a11y-missing-attribute -->
  <html>
    <body>
    <header style="background-color:#9DB2BF;padding:50px;margin:0px">
        <h1 >Header</h1>
        <h2>Subtitle 1</h2>
        <p>Subtitle 2</p>
    </header>

    

    <!-- <svg width="1000" height="200" xmlns="http://www.w3.org/2000/svg">
        <rect width="1000" height="100" x="0" y="0" rx="20" ry="20" fill="blue" />
      </svg> -->

    <div id="lorenzCurve"></div>
    <input type="range" name="range" class="slider" id="giniSlider" value="0.1"
		min="0.1" max="0.5" step="0.1" oninput="sliderChange(this.value)">
    <span id="giniVal">Gini Coefficient: 0.1</span>
        
        <br>
    <div></div>


    </body>
    </html>
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