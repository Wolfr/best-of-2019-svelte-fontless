<script>
    import { fade } from 'svelte/transition';

    import FancyTitle from '../components/FancyTitle.svelte';
    import items from './films.js';
</script>

<svelte:head>
    <title>Films - Best of 2019</title>
</svelte:head>

<div class="o-container-vertical">
    <div class="o-container o-container--medium">
        <FancyTitle line2="Films" />
        <div class="c-content">
          <p class="c-intro">I spent quite a bit less time in the cinema than in 2018 which was definitely my “year of films”. I stopped my habit of going to the cinema regularly. However, I kept listening to BBC’s film podcast and did discover some gems throughout 2019.</p>
        </div>
    </div>
</div>

{#each items as item}
<div class="o-container-vertical" in:fade='{{ duration: 500}}' out:fade='{{ duration: 0}}'>
    <div class="o-container o-container--large">
        <div class="o-grid">
            <div class="o-grid-col-bp3-6">
                <p><img src="/images/films/{ item.fileRef }" alt="{ item.filmName}"></p>
            </div>
            <div class="o-grid-col-bp3-6">
                <div class="c-content">
                    <h2>{ item.filmName }</h2>
                    <p><em>{ item.imdbDesc}</em></p>
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
            <a class="c-btn c-btn--md" href="/albums/">&larr; Previous: Albums</a>
            <a class="c-btn c-btn--md" href="/games/">Next: Games &rarr;</a>
        </div>
    </div>
</div>
