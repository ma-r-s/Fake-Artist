<script>
	import { playersStore, colors } from '$lib/stores.js';
	import DrawCanvas from './Canvas.svelte';
	let color = $colors[0];
	let currPlayer = 0;
	const nextPlayer = () => {
		currPlayer++;
		if (currPlayer < $playersStore) {
			color = $colors[currPlayer];
		} else {
			firstRound = false;
			currPlayer = 0;
			color = $colors[currPlayer];
		}
	};
	let firstRound = true;
</script>

<div class="flex justify-center flex-col items-center min-h-screen">
	<div class="flex items-center justify-around w-full mt-6">
		<p class="text-2xl font-bold">Player {currPlayer + 1}</p>
		{#if currPlayer < $playersStore - 1}
			<button class="btn" on:click={nextPlayer}>Next Player</button>
		{:else if firstRound}
			<button class="btn btn-primary" on:click={nextPlayer}>Next Round</button>
		{:else}
			<a class="btn btn-secondary" href="./vote">Vote</a>
		{/if}
	</div>
	<div class="border-black border-dashed border-4 grow m-6 w-11/12">
		<DrawCanvas {color} />
	</div>
</div>
