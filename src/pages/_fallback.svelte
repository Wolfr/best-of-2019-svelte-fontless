<script>
    import { url } from '@sveltech/routify'
</script>

<style>
    .c-404 {
        text-align: center;
        padding: 8rem 0;
    }
    h1 {
        font-size: 12.8rem;
        font-weight: 500;
        color: #000;
    }

    @media (prefers-color-scheme: dark) {
        h1 {
            color: #FFF;
        }
    }
    
</style>

<div class="c-404">
    <h1>404</h1>
    <p>Page not found.</p>
    <p><a href={$url('../')}>Go back</a></p>
</div>
