<script>
    import { afterUpdate } from 'svelte';
    import { isActive, url, context } from '@sveltech/routify';

    import Header from '../components/Header.svelte';
    import Footer from '../components/Footer.svelte';

    $: isSticky =
      $isActive("/index") ||
      $isActive("/disclaimer") ||
      $context.route.isFallback;

    afterUpdate(() => {
        window.scrollTo(0, 0);
    });

</script>

{#if isSticky}
  <div class="c-sticky-footer-layout">
      <div class="c-sticky-footer-layout__item">
          <Header />
      </div>
      <div class="c-sticky-footer-layout__item--grow">
          <div class="c-sticky-footer-layout__item-inner-center">
              <slot />
          </div>
      </div>
      <div class="c-sticky-footer-layout__item">
          <Footer />
      </div>
  </div>
{:else}
<Header />
<slot />
<Footer />
{/if}
