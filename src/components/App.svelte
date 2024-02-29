<script>
  import * as d3 from 'd3';
  import { onMount } from 'svelte';
  import Graph from './Graph.svelte';

  let data = [];

  onMount(async () => {
      const res = await fetch(
          '/gdp_gini_filtered_data.csv',
      );
      const csv = await res.text();
      await d3.csvParse(csv, (d) => {
          data.push({
             year: new Date(Date.UTC(d["Year"])),
             country_name: d["Country Code"],
             country_code: d["Country Name"],
             indicator_code: d["Indicator Code"],
             indicator_name: d["Indicator Name"],
             value: d["Value"],
          });
      });
      data = data;
  });

  $: console.log(data)
</script>

<main>
  <Graph {data} />
</main>