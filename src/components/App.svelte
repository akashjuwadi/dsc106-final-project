
<main>
  <!-- svelte-ignore a11y-missing-attribute -->
  <html>
    <head>
      
      <title>DSC 106 Final Group Project</title>
      
    </head>

    <body style="margin:100px">
      <h1>Two Methods for Measuring Economic Health</h1>
      <h2>Gross Domestic Product per Capita and the Gini Coefficient</h2>

      <div>
        <p>As data scientists, it is our responsibility to explore whatever data may apply towards the concept we look to better understand. This means putting our domain knowledge to good use by determining which metrics are sufficient for measuring a particular trait and which can be helpful but only tell a limited part of the story in which we aim to discover. Let's see how this idea applies in the case of the strength of each country's economy!</p>
      </div>
  
      <div>
        <h3>Gross Domestic Product (GDP)</h3>
        <p>There are many ways to measure the strength of a country's economy such as:</p>
        <ul>
          <li>Trade (imports and exports)</li>
          <li>Labor force participation (employed, unemployed, and not in the labor force)</li>
          <li>Income</li>
        </ul>
        <p>GDP tends to be the most popular statistic for indicating a nation's wealth given it measures the "monetary value of final goods and services" which is the sum of all consumption, investment, government purchases, and net exports (exports minus imports) over a given period of time.</p>
      </div>
  
      <div>
        <h3>Why could GDP possibly be flawed?</h3>
        <p>GDP doesn't give a full picture of how economic prosperity is distributed given:</p>
        <ul>
          <li>Large countries may have greater GDPs due to simply having a large population, leading many to prefer using GDP per capita.</li>
          <li>A high GDP per capita may also not indicate that all of the nation's people are benefitting much from the total wealth due to how it's distributed across the population.</li>
        </ul>
        <h3>The Gini Index</h3>
        <p>Economic inequality within a nation can be indicated with the Gini index which is derived from the Lorenz curve, a graph of the population's income distribution. The graph has the percent of the population on the x-axis and the proportion of overall income earned by said percent of the population on the y-axis. A line angled at 45 degrees (therefore having a slope of 1) represents perfect equality (so that half of the population earns exactly half of the income for example) an the Gini index is the area between the Lorenz curve and said line at 45 degrees, meaning a greater Gini index indicates greater inequality.</p>
      </div>
  
      <div id="lorenzCurve" align="center"><input type="range" name="range" class="slider" id="giniSlider" value="0.1"
        min="0.1" max="0.5" step="0.1" >
        <span id="giniVal" style="font-size:14px" align="center">Gini Coefficient: 0.1</span>
        <div id="lorenzInfo">The poorest 50% of the population owns 42% of the wealth.</div>
          <br></div>
      
      <!-- <input type="range" name="range" class="slider" id="giniSlider" value="0.1"
      min="0.1" max="0.5" step="0.1" >
      <span id="giniVal" style="font-size:14px" align="center">Gini Coefficient: 0.1</span>
      <div id="tooltip" opacity='0' position="absolute" marginTop=200 align="center"></div>
        <br> -->

      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>


      <div>
        <h2>Do these two metrics always agree for each country?</h2>
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
      <div style="display: contents">
        <svg id="scatterplot" width="400" height="300"></svg>
      </div>

      <br>
      <br>
      <br>
      <br>
      <br>
      <br>

      <div>
        <p>Notice how weak the correlation between the two metrics is throughout the years?</p>
        <p>If only one metric was satisfactory for measuring an economy's health, the correlation between the two would be nearly perfect given they would always be "agreeing" on the relative health of each economy when compared to that of another. However, it can be seen that this is not the case given it is fairly common for a country to have a more impressive GDP per capita than another (a greater value along the y-axis) but have a less impressive gini index (a greater value along the x-axis).</p> 
      </div>

      <div>
        <p>So why consider both metrics?</p>
        <ul>
          <li>GDP measures economic activity well, but fails to provide information on what proportion of the population is involved in said activity.</li>
          <li>The Gini index descrives wealth distribution well, but does not indicate the level of either cumulative or average wealth.</li>
          <li>A more accurate picture can be depicted by looking at both measures because each of their pros can be extracted and cons negated.</li>
        </ul>
        <p>This economics example is a reminder of why feature selection through the use of EDA is such as important first step of the data science process.</p>
      </div>

      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
  
      <div>
        <h2>Demo Writeup from 3/1/2024</h2>
        <h3>What have you done so far?</h3>
        <p>This demo contains two of our planned visualizations and pulls from two datasets we cleaned. One is a scatterplot that displays the gini index and GDP per capita data for each country for any year chosen by the user. The other is the Lorenz curve which is shaped by user input of the gini index. This demo also contains much of the background information and analysis that will make up the final product's text.</p>
        <h3>What will be the most challenging of your project to design and why?</h3>
        <p>The most challenging aspects of finishing the project will be adding more interactive elements to our visualizations without them interfering with how said visualizations are initially displayed. Making these visualizations (and therefore interactive components) aesthetically pleasing without impeding on how effectively they communicate our message will also be challenging due in part to the subjective nature of many of the design decisions that will need to be made. Significant time may also need to be invested into forming more of a storyline that helps viewers explore our topics and better understand the economics-related message we our aiming to convey. Continuing to become familiar with d3.js syntax as well as other technical skills (such as working with GeoJSON data) will also take some time in order to accomplish the previously-mentioned tasks.</p>
        <h2>Introduction Video from 3/8/2024</h2>
        <iframe width="800" height="600" src="https://www.youtube.com/embed/Fv5OA3sOYcE"></iframe>
      </div>
    </body>
    </html>
</main>

<script>
  import * as d3 from 'd3';
  import { onMount } from 'svelte';
  import Graph from './Graph.svelte';
  import { scaleLinear } from 'd3-scale';
  //import Scatter from './Graph.svelte';
  //import ChoroplethGDP from './Choropleth-GDP.svelte';
  //import gdpData from './data.json';
  //import ChoroplethGini from './Choropleth-Gini.svelte';
  //import giniData from './data.json';

  const width = 928;
  const height = 500;
  const marginTop = 10;
  const marginRight = 10;
  const marginBottom = 20;
  const marginLeft = 40;

  let data = [];

  onMount(async () => {
      const res = await fetch(
          'static/gdp_gini.csv',
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
width = 460 - margin.left - margin.right,
height = 400 - margin.top - margin.bottom;

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

// tooltip 
// d3.select('body')
  // .append('div')
  // .attr('id', 'tooltip')
  // .style("position", "absolute")
  // .style("opacity", 0);


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
        .style("fill", "lightblue")
        


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


// axis lables 
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
        const margin = { top: 20, right: 50, bottom: 50, left: 100 };
        const width = 1000 - margin.left - margin.right;
        const height = 600 - margin.top - margin.bottom;

        // Append SVG container to the body
        const svg = d3.select("#scatterplot")
            .attr("width", width + margin.left + margin.right)
            .attr("height", height + margin.top + margin.bottom)
            .append("g")
            .attr("transform", `translate(${margin.left},${margin.top})`);

        // Define scales for x and y axes
        var xScale = scaleLinear()
            .domain(d3.extent(filteredData, function(d){return d.gini}))
            .range([0, width]);
        // Add x-axis
        svg.append("g")
            .attr("transform", `translate(0,${height})`)
            .call(d3.axisBottom().scale(xScale));

        var yScale = scaleLinear()
            .domain(d3.extent(filteredData, function(d){return d.gdp}))
            .range([height, 0]);
        
        // Add y-axis with custom tick format
        svg.append("g")
          .call(d3.axisLeft().scale(yScale).tickFormat(d => `$${d3.format(",")(d)}`));

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
            .attr("cy", function(d){ return yScale(d.gdp)})
            .attr("r", 5) // radius of the circles
            .style("fill", function(d) { return colorScale(d.region); })
            .append("title")
            .text(d => `Country: ${d.country}\nGDP: $${d3.format(",.2f")(d.gdp)}\nGini: ${d3.format(",.3f")(d.gini)}`);
        // Add axis labels
     // Add axis labels
     svg.append("text")
        .attr("text-anchor", "middle")
        .attr("transform", `translate(${width / 2},${height + margin.top + 10})`)
        .text("Gini Index");

    svg.append("text")
        .attr("text-anchor", "middle")
        .attr("transform", `translate(${-margin.left + 10},${height / 2})rotate(-90)`)
        .text("GDP Per Capita (current US$)");

    svg.append("text")
        .attr("x", width / 2)
        .attr("y", margin.top / 4)
        .attr("text-anchor", "middle")
        .style("font-size", "1.5em")
        .text("GDP vs Gini");

    // Adding Legend
    const legend = svg.append("g")
        .attr("class", "legend")
        .attr("transform", `translate(${width - margin.right - 15},${margin.top+ 20})`);

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
        .text("Regions");
  }
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

  *,
  *::before,
  *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }


    main {
        text-align: left;
        color: #27323F;
        font-family:'Libre Baskerville', serif;
        font-size:12px;
        line-height: 1.8em;
        
    }

    h1 {
        font-family:'League Spartan', sans-serif;
        font-size: 24pt;
        padding:20px;
        text-align:center;
    }
    h2 {
        font-size: 12pt;
        padding:20px
    }
    h3 {
        font-size: 12pt;
        padding:20px
    }
    p {
        font-size: 10pt;
        padding:10px;
    }
    li {
      text-indent:5px;
      margin:25px;
    }
    
    body {background-color:#DDE6ED;}
</style>
