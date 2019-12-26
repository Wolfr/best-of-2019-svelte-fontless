<script>
    import FancyTitle from '../components/FancyTitle.svelte';
    import Slider from '../components/Slider.svelte';
    import items from './games.js';
</script>

<svelte:head>
    <title>Games - Best of 2019</title>
</svelte:head>

<div class="o-container-vertical">

    <div class="o-container o-container--medium">
        <FancyTitle line2="Games" />
    </div>

    <Slider />

    <div class="o-container o-container--medium">
        <div class="c-content">

            <p class="c-intro">2019 is the year that I properly got into sim racing. After visiting a friend and trying his rig I was convinced I wanted to spend some time exploring sim racing. It is a ton of fun, and combined with an interest in F1 and rally, a lot of my leisure time in 2019 had just one theme: racing.</p>

            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
          
        </div>
    </div>
</div>

<div class="o-container-vertical">

    <div class="o-container o-container--medium">
        <div class="c-content">
            <h3>Honorable Mentions</h3>
            <p>Observation: I have a penchant for deep simulation games, but these can take hundreds of hours, so I kind of only got to play them a little bit. Still; I find these games are still nice, even if it's only for a few hours.</p>
        </div>
    </div>

    <div class="o-container o-container--large">
        <div class="o-grid">
        {#each items as item}
            <div class="o-grid-col-bp2-2">
                <p><img src="/images/games/{ item.fileRef }" alt="{ item.gameName}"></p>
                <p>{ item.gameName }</p>
            </div>
        {/each}
        </div>
    </div>

</div>

<div class="o-container-vertical">
    <div class="o-container o-container--large">
        <div class="c-categories-nav">
            <a class="c-btn c-btn--md" href="/films/">&larr; Previous: Films</a>
            <a class="c-btn c-btn--md" href="/series/">Next: Series &rarr;</a>
        </div>
    </div>
</div>