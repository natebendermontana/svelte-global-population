<script>
    export let data;
    export let colorScale;
    import { fade } from "svelte/transition";
    import { format } from "d3-format";

    const suffixFormat = (d) => format(".2s")(d).replace("G", "B");
    const minColor = colorScale.range()[0];
    const maxColor = colorScale.range()[1];
    const minValue = colorScale.domain()[0];
    const maxValue = colorScale.domain()[1];
    
    $: percentofMax = (data?.population / maxValue) * 100;
</script>

<div class="legend">
<span class="label">{suffixFormat(minValue)}</span>
<div class="bar"
    style:background="linear-gradient(to right, {minColor} 0%, {maxColor} 100%)">
    {#if percentofMax}
    <span class="line" style:left={percentofMax + "%"}
    transition:fade
    />
    {/if}
</div>
<span class="label">{suffixFormat(maxValue)}</span>
</div>

<style>
.legend {
    display: flex;
    flex-direction: row;
    gap: 6px;
}

    .bar {
        height: 15px;
        width: 100%;
        position: relative;

    }

    .label {
        color: white;
        font-size: 0.85rem;
        user-select: none;
    }

    .line {
        position: absolute;
        top: 0px;
        height: 15px;
        width: 2px;
        background: white;
        transition: left 500ms cubic-bezier(1,0,0,1);
    }
</style>
