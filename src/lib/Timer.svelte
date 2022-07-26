<script>
    export let title;


    let timerState = 0;
	let elapsedTime = 0;
	let totalTime = 0;

	$: elapsedRounded = Math.round(elapsedTime/60000);
	$: totalRounded = Math.round(totalTime/60000);

	$: displayTime = elapsedTime === 0 ? '-': elapsedTime < 60000 ? '<1' : elapsedRounded

	let interval = 0;
	function handleStart() {
		let startTime = Date.now()
		interval = setInterval(() => {
			const now = Date.now()
			elapsedTime = now - startTime
			console.log(elapsedTime)
		}, 100)
		timerState = 1
	}

	function handleReset() {
		totalTime += elapsedTime
		clearInterval(interval)
		elapsedTime = 0
		timerState = 0
	}
</script>

<section>
    <h3>{title}: {totalRounded}min</h3>

    <p class="time">{displayTime}</p>
	{#if timerState === 0}
    <button on:click={handleStart}>Start</button>
	{:else}
	<button on:click={handleReset}>Reset</button>
	{/if}
	
</section>

<style>
    section{
        margin: .5em;
    }
</style>