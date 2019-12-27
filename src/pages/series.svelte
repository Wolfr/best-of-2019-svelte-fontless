<script>
    import { fade } from 'svelte/transition';

    import FancyTitle from '../components/FancyTitle.svelte';
    import items from './series.js';
</script>

<svelte:head>
    <title>Series - Best of 2019</title>
</svelte:head>

<div class="o-container-vertical">
    <div class="o-container o-container--medium">
         <FancyTitle line2="Series" />

        <div class="c-content">
          <p class="c-intro">Last year I said Netflix kept on releasing interesting series but I think I cancelled and restarted my subscription twice this year. There was a definite lack of good series and I would have to look elsewhere to find good content. I even re-watched Weeds and Mad Men because I was looking for something good. Luckily, Apple launched Apple TV+ with two fun series and at the end of the year, the Witcher landed on Netflix, so all in all, it wasn’t that bad.</p>
        </div>
    </div>
</div>

{#each items as item}
<div class="o-container-vertical" in:fade='{{ duration: 500}}' out:fade='{{ duration: 0}}'>
    <div class="o-container o-container--large">
        <div class="o-grid">
            <div class="o-grid-col-bp3-6">
                <p><img src="/images/series/{item.fileRef}" class="c-two-col__image" alt="{ item.seriesName}"></p>
            </div>
            <div class="o-grid-col-bp3-6">
                <div class="c-content">
                    <h2>{ item.seriesName }</h2>
                    <p><em>{ item.imdbDesc }</em></p>
                    <p>{ item.review }</p>
                    <p class="c-btn-toolbar">
                        <a href="{ item.trailerLink }" class="c-btn">Trailer</a>
                        <a href="{ item.imdbLink }" class="c-btn">IMDB</a>
                    </p>
                </div>
            </div>
        </div>
    </div>
</div>
{/each}

<div class="o-container-vertical">
    <div class="o-container o-container--large">
        <div class="c-categories-nav">
            <a class="c-btn c-btn--md" href="/games/">&larr; Previous: Games</a>
        </div>
    </div>
</div>
