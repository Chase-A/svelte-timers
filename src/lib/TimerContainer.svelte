<script>
    import Timer from "./Timer.svelte";

    let timers = [
        "applications",
        "portfolio",
        "bitwig",
        "guitar",
        "blender",
        "krita",
        "gx",
    ];
</script>

<section class="timer-container">
    {#each timers as timer}
        <Timer title={timer} />
    {/each}
</section>

<style>
    .timer-container{
        display: flex;
        /* margin: 0 auto; */
        place-content: center;
    }
</style>