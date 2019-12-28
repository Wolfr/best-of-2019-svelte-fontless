<script>
    
    let gridSize = 14;
    let dotSize = 1.5;
    let countCols = 30;
    let countRows = 10;

    let windowWidth;
    checkWindow();

    function checkWindow() {
        windowWidth = window.innerWidth;
        if (windowWidth < 1024) {
            countRows = 40;
            countCols = 80;
        } else {
            countRows = 20;
            countCols = 20;
        }
    }

</script>

<style>

    svg {
        width: 100%;
        height: 100%;
        min-width: 40rem;
        min-height: 40rem;
        cursor: default;
        user-select: none;
    }

    circle {
        fill: #D5D5D6;
    }
    
    @media (prefers-color-scheme: dark) {
        circle {
            fill: #AFC6FF;
        }
    }

</style>

<svelte:window on:resize={checkWindow}></svelte:window>

<svg>
    <g transform="translate(2,2)">
        {#each Array(countCols) as _, i}
            {#each Array(countRows) as _, j}
                <circle cx="{dotSize+(i*dotSize*gridSize)}" cy="{dotSize*gridSize*j}" r="{dotSize}" />
                <circle cx="{dotSize+(i*dotSize*gridSize)+10}" cy="{dotSize*gridSize*j+8}" r="{dotSize*1,2}" />
            {/each}
        {/each}
    </g>
</svg>
