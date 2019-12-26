<script>
    

    import { isActive, url } from '@sveltech/routify'  
    import { onMount, afterUpdate } from 'svelte';

    
    let narrow;
    let windowWidth;

    handleResize();
    function handleResize() {
        windowWidth = window.innerWidth;
        if (windowWidth < 1024) {
            narrow = true
        } else {
            narrow = false
        }
    }

    let mobileNavOpen = false;

    function toggleMenu() {
        mobileNavOpen = !mobileNavOpen;
    }

    let links = [];

    $: links = [
      ['/index', 'Intro'],
      ['/albums', 'Albums'],
      ['/films', 'Films'],
      ['/games', 'Games'],
      ['/series', 'Series']
    ].map(([path, name]) => {
      return {
        name,
        href: $url(path),
        active: $isActive(path)
      }
    });

    afterUpdate(() => {
        window.scrollTo(0, 0);
    });

</script>


<svelte:window on:resize={handleResize}></svelte:window>


<style type="text/scss">

    .c-mobile-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 2.4rem;
    }
    
    /* Mobile navigation
       ========================================================================== */

    .c-nav-toggle {
      margin: 1.6rem 0;
    }

    .c-nav-toggle button {
        background: none;
        border: none;
    }

    .sr-only {
      position: absolute;
      width: 1px;
      height: 1px;
      padding: 0;
      margin: -1px;
      overflow: hidden;
      clip: rect(0,0,0,0);
      border: 0;
    }

    @media (max-width: 1023px) {

      .c-nav-mobile {
        background: #0B101C;
        position: fixed;
        top: 6.4rem;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 10;
        overflow: auto;
        height: 100%;
        width: 100%;
      }

      .c-nav-mobile a {
        margin: 0 auto;
        border-bottom: 1px solid rgba(#FFF,0.13);
        text-align: center;
        padding: 2.4rem;
        display: block;
        color: #FFF;
      }

      .c-nav-mobile a:hover,
      .c-nav-mobile a:focus {
        background: rgba(#FFF,0.1);
      }


      .c-nav-mobile a:last-child {
          border: none;
      }
  }

</style>

{#if !narrow}
<header class="c-header">
    <p><a href="/">wolfr's Best of 2019</a></p>
    <nav class="c-nav">
        {#each links as {name, href, active}}
          <a {href} class:active>{name}</a>
        {/each}
    </nav>
</header>
{:else }
    <div class="c-mobile-header">
        <p><a href="/">wolfr's Best of 2019</a></p>
        <div class="c-nav-toggle">
            {#if mobileNavOpen}
            <button on:click={toggleMenu}>
                <span class="sr-only">Close menu</span>
                <svg
                    width="24" height="24" viewBox="0 0 24 24"
                    stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                >
                    <line x1="18" y1="6" x2="6" y2="18"></line>
                    <line x1="6" y1="6" x2="18" y2="18"></line>
                </svg>
            </button>
            {:else}
            <button on:click={toggleMenu}>
                <span class="sr-only">Open menu</span>
                <svg width="24" height="24" viewBox="0 0 24 24">
                    <path d="M21 13H3C2.4 13 2 12.6 2 12C2 11.4 2.4 11 3 11H21C21.6 11 22 11.4 22 12C22 12.6 21.6 13 21 13Z" fill="white" />
                    <path d="M21 7H3C2.4 7 2 6.6 2 6C2 5.4 2.4 5 3 5H21C21.6 5 22 5.4 22 6C22 6.6 21.6 7 21 7Z" fill="white" />
                    <path d="M21 19H3C2.4 19 2 18.6 2 18C2 17.4 2.4 17 3 17H21C21.6 17 22 17.4 22 18C22 18.6 21.6 19 21 19Z" fill="white" />
                </svg>
            </button>
            {/if}
        </div>
    </div>
    {#if mobileNavOpen}
    <nav class="c-nav-mobile">
        {#each links as {name, href, active}}
          <a {href} class:active on:click={toggleMenu}>{name}</a>
        {/each}
    </nav>
    {/if}
{/if}

<slot />

<footer class="c-footer">
    <ul>
        <li>©2019 Johan Ronsse</li>
        <li><a href="https://twitter.com/intent/tweet?text=Check%20out%20@wolfr_2%20%27s%20Best%20of%202019&url=https%3A%2F%2Fbestof2019.johanronsse.be">Tweet about this!</a></li>
        <li><a href="/disclaimer/">Disclaimer</a></li>
        <li><a href="https://johanronsse.be/blog/making-of-best-of-2019">Read the <em>Making of</em></a></li>
    </ul>
</footer>