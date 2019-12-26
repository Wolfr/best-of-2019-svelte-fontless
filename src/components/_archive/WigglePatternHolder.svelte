<script>
    import WigglePattern from './WigglePattern.svelte';
</script>

<style>
    div {
        margin-left: -4rem;
        margin-top: -4rem;
        cursor: default;
    }
</style>

<!-- @see https://github.com/sveltejs/svelte/issues/2968 -->
<div>
    {#each Array(360) as _, i}
      <WigglePattern let:hovering={hovering}></WigglePattern>
    {/each}
</div>
