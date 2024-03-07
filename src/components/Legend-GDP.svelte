<script>
    export let colorScale;

    let thresholds = colorScale.thresholds();

    thresholds.unshift(0);
</script>

<g class = "legend">
    <text class="legend-title" fill="currentColor" font-weight="bold" x="610" y="20">GDP per Capita</text>

    {#each thresholds as tick, i}
        {@const xPosition = 610 + (i * 30)}
        {@const yPosition = 30}
            
            <rect
				fill={colorScale(tick)}
				x={xPosition}
				y={yPosition}
				height="10"
				width="30"
			/>

			{#if i !== 0}
				<line
                stroke="currentColor"
                x1={xPosition}
                x2={xPosition}
                y1={yPosition}
                y2={yPosition + 20}
                />

				<text
                fill="currentColor"
                text-anchor="middle"
                dominant-baseline="middle"
                x={xPosition}
                y={yPosition + 30}
                >{tick}</text>
			{/if}
	{/each}
</g>
