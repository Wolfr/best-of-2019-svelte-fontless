<script>
    import { fade, scale } from 'svelte/transition';

    const animate = (node, args) => args.cond ? fade(node, {delay: 0, duration: 300}) : scale(node, args);

    let hovering;

    function enter() {
        hovering = true;
    }

     function leave() {
         hovering = false;
     }

</script>

<style>
     svg {
          user-select: none;
          cursor: default;
     }
</style>

<svg width="21" height="21" viewBox="0 0 21 21" fill="none" class:active={hovering} on:mouseenter={enter} on:mouseleave={leave}>
     {#if hovering}
        <circle cx="4.5" cy="4.5" r="2.5" transition:animate fill="#AFC6FF"/>
        <circle cx="17.5" cy="17.5" r="1.5" transition:animate fill="#AFC6FF"/>
    {:else}
        <circle cx="4.5" cy="4.5" r="2.5" transition:animate fill="#AFC6FF"/>
        <circle cx="17.5" cy="17.5" r="1.5" transition:animate fill="#AFC6FF"/>
     {/if}
</svg>
