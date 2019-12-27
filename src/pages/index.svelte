<script>
    import { fade, fly } from 'svelte/transition';
    import { expoInOut } from 'svelte/easing';

    import Header from '../components/Header.svelte';
    import Footer from '../components/Footer.svelte';
    
    import Wiggle from '../components/Wiggle.svelte';
</script>

<svelte:head>
    <title>Intro - Best of 2019</title>
</svelte:head>

<style>

    h1 {
      font-size: 9.6rem;
      margin: 0 0 3.2rem;
      line-height: 1;
      font-weight: 500;
      color: #000;
    }

    @media (prefers-color-scheme: dark) {
        h1 {
            color: #FFF;
        }
    }

    .o-container-home {
        margin: 8rem auto;
        max-width: 128rem;
    }

    .text {
        padding: 2.4rem;
        flex: 1 0 60%;
    }

</style>

<div class="o-container-vertical">
    <div class="o-container-home">
        <div class="o-grid">
            <div class="o-grid-col-bp3-6" in:fly="{{ x: -700, duration: 600, easing: expoInOut }}">
                <h1>Best of 2019</h1>
                <div class="c-content">
                    <p class="c-intro">Just like last year, I've compiled some lists of my favorite “media consumed” this year. I always use this as an exercise to test out some technical things I didn't get to during the year, while also revisiting some of my favorite content and/or releases. Enjoy.</p>
                    <a href="/albums" class="c-btn c-btn--lg u-spacer-top">Dive in &rarr;</a>
                </div>
            </div>
            <div class="o-grid-col-bp3-6" in:fade='{{ duration: 500}}' out:fade='{{ duration: 0}}'>
                <div>
                    <Wiggle />
                </div>
            </div>
        </div>
    </div>
</div>
