<style>
    
    /* Wrapper */
    
    .extra-outer-wrapper {
        max-width: 128rem;
        margin: 0 auto;
    }

    .outer-wrapper {
        width: 100%;
        /* Change this to the aspect ratio of the images,
           divide the height by the width and set in % */
        padding: 0 0 47.177%;
        position: relative;
    }
    
    .inner-wrapper {
        height: 100%;
        width: 100%;
        display: flex;
        position: absolute;
    }

    .slide {
        flex: 1 0 auto;
        width: 100%;
        height: 100%;
        align-items: center;
        justify-content: center;
        display: flex;
        text-align: center;
        font-weight: 700;
        font-size: 2rem;
        color: #FFF;
    }

    /* Dots at the bottom */

    .dots {
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 0 0 8rem;
    }
    
    .dot {
        display: inline-block;
        font-size: 0;
        padding: 0.9rem 0.2rem;
        margin: 0.3rem;
        background: transparent;
        border: none;
    }
    .dot-inner {
        width: 0.8rem;
        height: 0.8rem;
        background: #FFF;
        border-radius: 100%;
        opacity: 0.3;
    }

    .dot.selected .dot-inner {
        opacity: 1;
    }

    /* Controls */

    .controls {
        text-align: center;
        width: 100%;
        display: block;
    }

    .controls button {
        background: transparent;
        padding: 0;
        margin: 0;
        width: 4.8rem;
        height: 4.8rem;
        border-color: transparent;
    }

    .controls button svg {
        width: 100%;
        height: 100%;
    }
    
    .controls button:hover,
    .controls button:focus {
    }

    .controls button:first-child {
        position: absolute;
        left: 2rem;
        top: calc(50% - 1.2rem);
    }
    
    .controls button:last-child {
        position: absolute;
        right: 2rem;
        top: calc(50% - 1.2rem);
    }

</style>

<script>
    import { hslide } from './hslide.js';

    let slides = [
        { content: '/images/games/acc.jpg', alt: 'Assetto Corsa: Competizione' },
        { content: '/images/games/dr2.jpg', alt: 'Dirt Rally 2.0'  },
        { content: '/images/games/gt.jpg', alt: 'Gran Turismo Sport' }
    ]

    let cur = 0;

    function changeSlide(slide) {
        cur = slide;
    }

    const clamp = (number, min, max) => Math.min(Math.max(number, min), max);
    const transition_args = {
        duration: 200,
    }

    function prev(e) {
        cur = clamp( --cur, 0, slides.length-1 )
    }

    function next(e) {
        cur = clamp( ++cur, 0, slides.length-1 )
    }

  const ARROW_LEFT = 37;
    const ARROW_RIGHT = 39;
    function handleShortcut(e) {
        if (e.keyCode === ARROW_LEFT ) {
            prev();
        }
        if (e.keyCode === ARROW_RIGHT ) {
            next();
        }
    }

</script>

<svelte:window on:keyup={handleShortcut} />

<div class="extra-outer-wrapper">
    <div class="outer-wrapper">
        <div class="inner-wrapper">
            {#each slides as slide, id}
                {#if id === cur}
                <div
                    class="slide"
                    in:hslide={transition_args}
                    out:hslide={transition_args}
                >
                    <img src="{slide.content}" alt="{slide.alt}" />
                </div>
                {/if}
            {/each}
            <div class="controls">
                <button on:click="{()=>prev()}">
                    <!--Left button -->
                    <svg width="78" height="78" viewBox="0 0 78 78" fill="none">
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M39 78C17.4609 78 0 60.5391 0 39C0 17.4609 17.4609 0 39 0C60.5391 0 78 17.4609 78 39C78 60.5391 60.5391 78 39 78ZM27.8384 39.7907L38.7906 28.8383L41.114 31.1617L32.9662 39.3095H52V42.5952H32.9662L41.114 50.7431L38.7906 53.0664L27.8384 42.1141L26.6766 40.9524L27.8384 39.7907Z" fill="white"/>
                    </svg>
                </button>
                <button on:click="{()=>next()}">
                    <!--Right button -->
                    <svg width="78" height="78" viewBox="0 0 78 78" fill="none">
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M39 78C60.5391 78 78 60.5391 78 39C78 17.4609 60.5391 0 39 0C17.4609 0 0 17.4609 0 39C0 60.5391 17.4609 78 39 78ZM50.1616 39.7907L39.2094 28.8383L36.886 31.1617L45.0338 39.3095H26V42.5952H45.0338L36.886 50.7431L39.2094 53.0664L50.1616 42.1141L51.3234 40.9524L50.1616 39.7907Z" fill="white"/>
                    </svg>
                </button>
            </div>
        </div>
    </div>

    <div class="dots">
        {#each slides as slide, i}
            <button class="dot" class:selected={cur == i}  on:click={()=>changeSlide(i)}>
                <div class="dot-inner">
                    {i+1}
                </div>
            </button>
        {/each}
    </div>
</div>
