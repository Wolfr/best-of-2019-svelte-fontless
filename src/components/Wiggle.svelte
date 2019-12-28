<script>
    import { fade, fly } from 'svelte/transition';
    import { expoInOut } from 'svelte/easing';
    import WigglePatternHolder from './WigglePatternholder.svelte';
</script>
<style>

    /* Z-holder - Do not show on mobile */

    .z-holder {
        display: none;
    }

    @media (min-width: 1024px) {
        .z-holder {
            display: block;
        }
    }

    /* Z-holder */

    .z-holder {
        position: relative;
        min-height: 20rem;
        min-width: 100%;
    }

    .z-holder-child {
        position: absolute;
        top: 0;
        left: 0;
    }

    @media (min-width: 1024px) {
        .z-holder {
            min-width: 100%;
            min-height: 40rem;
        }

        .z-holder-child {
            position: absolute;
            top: -2rem;
            left: 5rem;
        }
    
    }


    .box {
        background: #0D0D0D;
        opacity: 0.1;
        width: 80%;
        min-width: 28rem;
        min-height: 14rem;
	}
    
    @media (prefers-color-scheme: dark) {

        .box {
            background: #3C5597;
            opacity: 0.2;
        }
    }
    
    @media (min-width: 1024px) {
        .box {
            width: 58.4rem;
            height: 40.9rem;
        }
    }

    .globe {
        width: 80%;
        height: 80%;
        border-radius: 100%;
        border: 0.2rem solid #000;
        opacity: 0.1;
        pointer-events: none;
        margin-top: 5%;
        margin-left: 5%;
    }

    @media (min-width: 1024px) {
        .globe {
            width: 44.4rem;
            height: 44.4rem;
            margin-top: 10rem;
            margin-left: 10rem;
        }
    }
    
    @media (prefers-color-scheme: dark) {
        .globe {
            border: 0.2rem solid #ECF1FF;
            opacity: 0.4;
        }
    }
    
    .wiggle {
        margin-top: -4rem;
        margin-left: -4rem;
    }

</style>

<div class="z-holder">
    <div class="z-holder-child"  in:fly="{{ x: 200, duration: 600, easing: expoInOut }}">
        <div class="globe"></div>
    </div>
    <div class="z-holder-child"  in:fly="{{ x: 600, duration: 800, easing: expoInOut }}">
        <div class="box"></div>
    </div>
    <div class="z-holder-child" in:fly="{{ x: 1200, duration: 400, easing: expoInOut }}" >
        <div class="wiggle">
            <WigglePatternHolder />
        </div>
    </div>
</div>
