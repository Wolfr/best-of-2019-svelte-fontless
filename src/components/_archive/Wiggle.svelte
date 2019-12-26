<script>
    import WigglePatternHolder from './WigglePatternholder.svelte';
</script>
<style>
	.box {
        background: #3C5597;
        opacity: 0.2;
        width: 58.4rem;
        height: 40.9rem;
	}
    
    .z-holder {
        position: relative;
        min-width: 40rem;
        min-height: 40rem;
    }

    .z-holder-child {
        position: absolute;
        top: 0;
        left: 0;
    }

    .globe {
        width: 44.4rem;
        height: 44.4rem;
        border-radius: 100%;
        border: 0.2rem solid #ECF1FF;
        opacity: 0.3;
        pointer-events: none;
        margin-top: 10rem;
        margin-left: 10rem;
    }

</style>

<div class="z-holder">
    <div class="z-holder-child">
        <div class="globe"></div>
    </div>
    <div class="z-holder-child">
        <div class="box"></div>
    </div>
    <div class="z-holder-child">
        <WigglePatternHolder />
    </div>
</div>
