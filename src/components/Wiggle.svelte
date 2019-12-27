<script>
    import { fade, fly } from 'svelte/transition';
    import { expoInOut } from 'svelte/easing';

    import WigglePatternHolder from './WigglePatternholder.svelte';
</script>
<style>

    .z-holder {
        display: none;
    }
    
    @media (min-width: 1024px) {
        .z-holder {
            display: block;
        }
    }

	.box {
        background: #0D0D0D;
        opacity: 0.1;
        width: 58.4rem;
        height: 40.9rem;
	}
    
    @media (prefers-color-scheme: dark) {
        .box {
            background: #3C5597;
            opacity: 0.2;
        }
    }

    .z-holder {
        position: relative;
        min-width: 40rem;
        min-height: 40rem;
        margin-left: 4rem;
    }

    .z-holder-child {
        position: absolute;
        top: 0;
        left: 0;
    }

    .globe {
        width: 44.4rem;
        height: 44.4rem;
        border-radius: 100%;
        border: 0.2rem solid #999;
        opacity: 0.3;
        pointer-events: none;
        margin-top: 10rem;
        margin-left: 10rem;
    }

    @media (prefers-color-scheme: dark) {
        .globe {
            border: 0.2rem solid #ECF1FF;
        }
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
        <WigglePatternHolder />
    </div>
</div>
