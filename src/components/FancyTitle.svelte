<script>
   export let line1 = "Best of 2019";
   export let line2 = "Albums";
</script>
   
<style>

    h1 {
      margin: 0 0 3.2rem;
      line-height: 1;
      color: #000;
      font-weight: 500;
      font-size: 8.5rem;
    }
    
    @media (prefers-color-scheme: dark) {
        h1 {
            color: #FFF;
        }
    }
    
    @media (min-width: 800px) {
        h1 {
            font-size: 9.6rem;
        }
    }
    
    span {
        display: block;
        font-size: 3.2rem;
        opacity: 0.5;
    }

</style>

<h1>
    <span>{line1}</span>
    {line2}
</h1>