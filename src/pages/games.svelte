<script>

    import FancyTitle from '../components/FancyTitle.svelte';
    import Slider from '../components/Slider.svelte';
    import items from './games.js';
    
    let modalShowing = false;
    let currentFileRef = false;
    let currentGameName = false;

    function showModal(fileRef, gameName) {
        modalShowing = !modalShowing;
        currentFileRef = fileRef;
        currentGameName = gameName;
    }

</script>

<style>

    .modal-backdrop {
        position: fixed;
        background: rgba(0,0,0,0.3);
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        width: 100%;
        height: 100%;
    }

    .modal {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        width: 100%;
        height: 100%;
        display: flex;
    }

    .modal img {
        margin: auto;
        display: block;
    }
</style>

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

            <p>Looking back at the blog posts on my blog about sim racing (<a href="https://johanronsse.be/2019/05/10/sim-racing-1/">1</a>, <a href="https://johanronsse.be/2019/05/30/sim-racing-2/">2</a>, <a href="https://johanronsse.be/2019/09/21/sim-racing-3/">3</a>, <a href="https://johanronsse.be/2019/10/26/sim-racing-4/">4</a>) I was clearly always going a bit deeper into sim racing. The past few weeks have been so busy with work that I haven't had much time to race. I think I reached a point where I believe I need to put hundred of hours into it to improve just a little bit. For me, it's always been about the fun. Of course, being competitive is also fun. But I can't justify it to myself to spend hours and hours behind the sim rig to shave off a few seconds off a track time. So I think in 2020 I am just going to race less, but focus on the parts that are fun to me: discovering new tracks, new cars, maybe some racing with friends. </p>
          
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
                <a href="/images/games/{ item.fileRef }" on:click|preventDefault="{() => showModal(item.fileRef, item.gameName)}">
                    <img src="/images/games/{ item.fileRef }" alt="{item.gameName}">
                </a>
                <p>{ item.gameName }</p>
            </div>
        {/each}
        </div>

        {#if modalShowing}
            <div class="modal-backdrop" on:click|preventDefault={showModal}></div>
            <div class="modal" on:click|preventDefault={showModal}>
                <img src="/images/games/{ currentFileRef }" on:click|preventDefault={showModal} class="modal-image" alt="{currentGameName}">
            </div>
        {/if}

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

