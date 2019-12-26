<script>
    import FancyTitle from '../components/FancyTitle.svelte';
    import items from './albums.js'
</script>

<svelte:head>
    <title>Albums - Best of 2019</title>
</svelte:head>

<div class="o-container-vertical">
    <div class="o-container o-container--medium">
        <FancyTitle line2="Albums" />
        <div class="c-content ">
            <p class="c-intro">Spotify’s Wrapped told me that I listened to Spotify for +-74000 minutes. That’s less than the 94k and 92k of 2018 and 2017. I think as my job moves towards management, I have more meetings, and this changes how much I can listen to music. I re-discovered Mac Miller (RIP), enjoyed Marc Martell’s Queen cover album and enjoyed releases from artists that are there to stay: The National and Calexico.</p>
        </div>
    </div>
</div>

<div class="o-container-vertical">
    <div class="o-container o-container--large">
        <ul class="c-cards">
        {#each items as item}
              <li class="c-card">
                  <div class="c-card__image">
                      <img src="/images/albums/{ item.fileName }" alt="">
                  </div>
                  <div class="c-card__body">
                      <h2 class="c-card__heading">{ item.artistName } - { item.albumName }</h2>
                      <p class="c-card__meta">{ item.releaseDate }</p>
                      {#if item.categories}
                      <ul>
                          {#each item.categories as category}
                          <li class="c-card__category">{ category }</li>
                          {/each}
                      </ul>
                      {/if}
                </div>
              </li>
              {/each}
        </ul>
    </div>
</div>

<div class="o-container-vertical">
    <div class="o-container o-container--large">
        <div class="c-categories-nav">
            <a class="c-btn c-btn--md" href="/">&larr; Previous: Intro</a>
            <a class="c-btn c-btn--md" href="/films/">Next: Films &rarr;</a>
        </div>
    </div>
</div>