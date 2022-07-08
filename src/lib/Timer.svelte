<script>
    export let title;


    let timerState = 0;
	let elapsedTime = 0;
	// rounded dependent var ??^
	$: elapsedRounded = Math.round(elapsedTime/1000);

	let interval = 0;
	function handleStart() {
		let startTime = Date.now()
		interval = setInterval(() => {
			const now = Date.now()
			elapsedTime = now - startTime
			console.log(elapsedTime)
		}, 1000)
		timerState = 1
	}

	function handleReset() {
		clearInterval(interval)
		elapsedTime = 0
	}
</script>

<section>
    <h3>{title}</h3>
    <p class="time">{elapsedRounded}</p>
    <button on:click={handleStart}>Start</button>
	<button on:click={handleReset}>Reset</button>
</section>

<style>
    section{
        margin: .5em;
    }
</style>