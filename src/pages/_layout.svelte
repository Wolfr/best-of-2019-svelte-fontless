<script>
    import { isActive, url } from '@sveltech/routify'
    import Header from '../components/Header.svelte';
    import Footer from '../components/Footer.svelte';
    $: console.log($url());
</script>

{#if (
    $isActive('/index') || $isActive('/disclaimer')
) }
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