<!-- src/App.svelte -->
<script>
    import LeftSide from './leftside.svelte';
    import RightForm from './rightside.svelte';
</script>

<style>
    .container {
        display: flex;
        width: 100vw;
        height: 100vh;
        overflow: hidden;
    }

    @media (max-width: 768px) {
        .container {
            flex-direction: column; /* Stack the components vertically on small screens */
            height: auto;
        }
    }
</style>

<div class="container">
    <LeftSide />
    <RightForm />
</div>
