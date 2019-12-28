<script>
    import Brand from '../components/Brand.svelte';

    import { isActive, url } from '@sveltech/routify'  
    import { afterUpdate } from 'svelte';

    // Mobile menu

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
        if (mobileNavOpen) {
          document.documentElement.classList.add('u-kill-scroll');
          document.body.classList.add('u-kill-scroll');
        } else {
          document.documentElement.classList.remove('u-kill-scroll');
          document.body.classList.remove('u-kill-scroll');
        }
    }

    // Main nav

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

</script>

<svelte:window on:resize={handleResize}></svelte:window>

{#if !narrow}
<header class="c-header">
    <div class="o-container">
        <div class="c-nav-logo-holder">
            <Brand />
            <nav class="c-nav">
                {#each links as {name, href, active}}
                  <a {href} class:active>{name}</a>
                {/each}
            </nav>
        </div>
    </div>
</header>
{:else }
    <div class="c-mobile-header">
        <div class="o-container">
            <div class="c-nav-logo-holder">
                <Brand />
                <div class="c-nav-toggle">
                    {#if mobileNavOpen}
                    <button on:click={toggleMenu}>
                        <span class="u-sr-only">Close menu</span>
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
                        <span class="u-sr-only">Open menu</span>
                        <svg width="24" height="24" viewBox="0 0 24 24">
                            <path d="M21 13H3C2.4 13 2 12.6 2 12C2 11.4 2.4 11 3 11H21C21.6 11 22 11.4 22 12C22 12.6 21.6 13 21 13Z" fill="white" />
                            <path d="M21 7H3C2.4 7 2 6.6 2 6C2 5.4 2.4 5 3 5H21C21.6 5 22 5.4 22 6C22 6.6 21.6 7 21 7Z" fill="white" />
                            <path d="M21 19H3C2.4 19 2 18.6 2 18C2 17.4 2.4 17 3 17H21C21.6 17 22 17.4 22 18C22 18.6 21.6 19 21 19Z" fill="white" />
                        </svg>
                    </button>
                    {/if}
                </div>
            </div>
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