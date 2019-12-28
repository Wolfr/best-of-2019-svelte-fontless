<style>

    /* Wrapper */

    .slider-extra-outer-wrapper {
        max-width: 128rem;
        margin: 0 auto;
    }

    .slider-outer-wrapper {
        width: 100%;
        /* Change this to the aspect ratio of the images,
           divide the height by the width and set in % */
        padding: 0 0 47.177%;
        position: relative;
    }
    
    .slider-inner-wrapper {
        height: 100%;
        width: 100%;
        display: flex;
        position: absolute;
    }

    .slider__slide {
        flex: 1 0 auto;
        width: 100%;
        height: 100%;
        align-items: center;
        justify-content: center;
        display: flex;
        text-align: center;
        font-weight: 700;
        font-size: 2rem;
        color: #000;
    }
    
    @media (prefers-color-scheme: dark) {
        slider__slide {
            color: #FFF;
        }
    }

    /* Dots at the bottom */

    .slider-dots {
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 2.4rem 0 4rem;
    }
    
    .slider-dots__dot {
        display: inline-block;
        font-size: 0;
        padding: 0.9rem 0.2rem;
        margin: 0.3rem;
        background: transparent;
        border: none;
    }

    .slider-dots__dot-inner {
        width: 0.8rem;
        height: 0.8rem;
        background: #000;
        border-radius: 100%;
        opacity: 0.3;
    }
    
    @media (prefers-color-scheme: dark) {
        .slider-dots__dot-inner {
            background: #FFF;
        }
    }

    .slider-dots__dot.selected .slider-dots__dot-inner {
        opacity: 1;
    }

    /* Controls */

    .slider-controls {
        text-align: center;
        width: 100%;
        display: block;
    }

    .slider-controls button {
        background: transparent;
        padding: 0;
        margin: 0;
        width: 4.8rem;
        height: 4.8rem;
        border-color: transparent;
    }

    .slider-controls button svg {
        width: 100%;
        height: 100%;
    }
    
    
    @media (prefers-color-scheme: dark) {
        .slider-controls button svg path {
            fill: #FFF;
        }
    }
    
    
    @media (max-width: 1024px) {
        .slider-controls button svg path {
            fill: #FFF;
        }
    }

    .slider__btn-prev {
        position: absolute;
        left: 2rem;
        top: calc(50% - 1.2rem);
    }
    
    .slider__btn-next {
        position: absolute;
        right: 2rem;
        top: calc(50% - 1.2rem);
    }

</style>

<script>
    import { fade } from 'svelte/transition';

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
    function prev(e) { cur = clamp( --cur, 0, slides.length-1 ) }
    function next(e) { cur = clamp( ++cur, 0, slides.length-1 ) }

    // Shortcuts 
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

<div class="slider-extra-outer-wrapper">
    <div class="slider-outer-wrapper">
        <div class="slider-inner-wrapper">
            {#each slides as slide, id}
                {#if id === cur}
                <div
                    class="slider__slide"
                    in:hslide|local={ { duration: 200 } }
                    out:hslide|local={ { duration: 100 }}
                >
                    <img src="{slide.content}" alt="{slide.alt}" />
                </div>
                {/if}
            {/each}
            <div class="slider-controls">
                {#if cur != 0}
                    <button on:click="{()=>prev()}" class="slider__btn-prev">
                        <svg width="86" height="86" viewBox="0 0 86 86" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path fill-rule="evenodd" clip-rule="evenodd" d="M43 82C21.4609 82 4 64.5391 4 43C4 21.4609 21.4609 4 43 4C64.5391 4 82 21.4609 82 43C82 64.5391 64.5391 82 43 82ZM31.8384 43.7907L42.7906 32.8383L45.114 35.1617L36.9662 43.3095H56V46.5952H36.9662L45.114 54.7431L42.7906 57.0664L31.8384 46.1141L30.6766 44.9524L31.8384 43.7907Z" fill="black"/>
                        </svg>
                    </button>
                {/if}
                {#if cur != slides.length-1}
                    <button on:click="{()=>next()}" class="slider__btn-next">
                        <!--Right button -->
                        <svg width="86" height="86" viewBox="0 0 86 86" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path fill-rule="evenodd" clip-rule="evenodd" d="M43 82C64.5391 82 82 64.5391 82 43C82 21.4609 64.5391 4 43 4C21.4609 4 4 21.4609 4 43C4 64.5391 21.4609 82 43 82ZM54.1616 43.7907L43.2094 32.8383L40.886 35.1617L49.0338 43.3095H30V46.5952H49.0338L40.886 54.7431L43.2094 57.0664L54.1616 46.1141L55.3234 44.9524L54.1616 43.7907Z" fill="black"/>
                        </svg>
                    </button>
                {/if}
            </div>
        </div>
    </div>

    <div class="slider-dots">
        {#each slides as slide, i}
            <button class="slider-dots__dot" class:selected={cur == i}  on:click={()=>changeSlide(i)}>
                <div class="slider-dots__dot-inner">
                    {i+1}
                </div>
            </button>
        {/each}
    </div>
</div>
