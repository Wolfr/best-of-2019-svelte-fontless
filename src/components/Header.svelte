<script>
    import Brand from '../components/Brand.svelte';

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

{#if !narrow}
<header class="c-header">
    <div class="o-container">
        <div class="c-nav-logo-holder">
            <Brand />
            <nav class="c-nav">
                <!-- Light/dark mode @todo-->
                <!-- <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M16.1667 11.9997C16.1667 14.3013 14.3013 16.1667 11.9997 16.1667C9.69853 16.1667 7.83334 14.3013 7.83334 11.9997C7.83334 9.69853 9.69868 7.83334 11.9997 7.83334C14.3013 7.83334 16.1667 9.69868 16.1667 11.9997" fill="#F2FFA2"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M13.8946 3.83594C13.8946 4.85 13.0727 5.67267 12.0579 5.67267C11.0438 5.67267 10.222 4.85 10.222 3.83594C10.222 2.82188 11.0438 2 12.0579 2C13.0727 2 13.8946 2.82188 13.8946 3.83594" fill="#F2FFA2"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M7.56715 4.8876C8.28355 5.60478 8.28355 6.76729 7.56715 7.48441C6.84997 8.20159 5.68746 8.20159 4.97034 7.48441C4.25316 6.76723 4.25316 5.60472 4.97034 4.8876C5.68752 4.1712 6.85003 4.1712 7.56715 4.8876Z" fill="#F2FFA2"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M3.83594 10.1054C4.85 10.1054 5.67267 10.9273 5.67267 11.9421C5.67267 12.9562 4.85 13.7781 3.83594 13.7781C2.82188 13.7781 2 12.9562 2 11.9421C2 10.9273 2.82188 10.1054 3.83594 10.1054" fill="#F2FFA2"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M4.88756 16.4328C5.60475 15.7164 6.76725 15.7164 7.48437 16.4328C8.20155 17.15 8.20155 18.3125 7.48437 19.0296C6.76719 19.7468 5.60469 19.7468 4.88756 19.0296C4.17116 18.3124 4.17116 17.1499 4.88756 16.4328Z" fill="#F2FFA2"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M13.7781 20.164C13.7781 21.1781 12.9563 22 11.9422 22C10.9274 22 10.1055 21.1781 10.1055 20.164C10.1055 19.15 10.9274 18.3273 11.9422 18.3273C12.9563 18.3273 13.7781 19.15 13.7781 20.164" fill="#F2FFA2"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M16.4328 19.1124C15.7164 18.3952 15.7164 17.2327 16.4328 16.5156C17.15 15.7984 18.3125 15.7984 19.0296 16.5156C19.7468 17.2328 19.7468 18.3953 19.0296 19.1124C18.3124 19.8288 17.1499 19.8288 16.4328 19.1124Z" fill="#F2FFA2"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M20.1641 13.8946C19.15 13.8946 18.3273 13.0727 18.3273 12.0579C18.3273 11.0438 19.15 10.222 20.1641 10.222C21.1781 10.222 22 11.0438 22 12.0579C22 13.0727 21.1781 13.8946 20.1641 13.8946Z" fill="#F2FFA2"/>
                    <path fill-rule="evenodd" clip-rule="evenodd" d="M19.1124 7.56721C18.3952 8.28361 17.2327 8.28361 16.5156 7.56721C15.7984 6.85003 15.7984 5.68753 16.5156 4.97041C17.2327 4.25323 18.3952 4.25323 19.1124 4.97041C19.8288 5.68759 19.8288 6.85009 19.1124 7.56721Z" fill="#F2FFA2"/>
                </svg>
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12.0605 21.9999C15.754 21.9999 19.1414 19.975 20.9054 16.714C21.0515 16.4461 21.026 16.1185 20.8451 15.8762C20.6642 15.6339 20.3523 15.5174 20.0612 15.5837C19.4581 15.7153 18.8504 15.7806 18.2521 15.7806C13.5587 15.7806 9.73882 11.9439 9.73882 7.22771C9.73882 5.80397 10.0959 4.39525 10.7687 3.14866C10.9147 2.88075 10.8893 2.55323 10.7084 2.31089C10.5275 2.06855 10.2156 1.95211 9.92443 2.01839C5.33192 3.01709 2 7.16713 2 11.8927C2 17.4666 6.51243 22 12.0604 22L12.0605 21.9999Z" fill="#0B101C"/>
                </svg> -->
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