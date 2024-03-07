<script>
    import * as d3 from 'd3';
    import { scaleQuantize } from 'd3-scale';
    import { geoPath } from 'd3-geo';
    import { schemeBlues } from 'd3-scale-chromatic';
    import data from './gdp_gini_filtered_data_with_na.csv';
    import Legend from './Legend.svelte';
    import world from './countries.geojson';
    import { onMount } from 'svelte';

    const width = 975;
    const height = 610;

    const margin = {top: 10, right: 10, bottom: 20, left: 55};

    const colorScale = scaleQuantize([1, 10], schemeBlues[9]);

    const path = geoPath();

    onMount(async () => {
        const data = await fetch('./gdp_gini_filtered_data_with_na.csv');
    });

    var valuemap = new Map(data.Map(d => [d[1], d[2], d[5], d[6]])); // [country name, three letter country code, year, value]
    valuemap = valuemap.slice(13609) // 13610th row and onwards, 1st row is column labels and 2nd row is first data row

    const wfeats = world.features;

    wfeats.forEach(feature => {
        const props = feature.properties;
        console.log(props);
    });
    const countries = topojson.feature(world, world.objects.countries); // correct syntax?
    const countrymap = new Map(countries.features.Map(d => [d.ISO_A3, d])); // correct syntax?
    const countrymesh = topojson.mesh(world, world.objects.propeties, (a, b) => a !== b); // correct syntax?
</script>

<svg {width} {height} viewBox = "0 0 {width} {height}" style:max-width="100%" style:height="auto">
    <g class="data">
        {#each countries as country}
            <path fill={colorScale(valuemap.get(country.id))} d={path(country)}/>
        {/each}
    </g>

    <path fill="none" stroke="white" stroke-linejoin="round" d={path(countrymesh)} />

    <Legend {colorScale} />
</svg>