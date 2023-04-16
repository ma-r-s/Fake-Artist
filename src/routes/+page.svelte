<script>
	let players = 5;
</script>

<div class="w-full min-h-screen flex flex-col items-center justify-center">
	<p class="font-bold text-5xl m-4">Fake Artist</p>
	<p class="text-2xl m-2">Select number of players</p>
	<div class="flex items-center gap-4 m-2">
		{#if players > 4}
			<button
				class="btn btn-secondary aspect-square text-2xl"
				on:click={() => {
					players--;
				}}
			>
				{'<'}
			</button>
		{:else}
			<p class="btn aspect-square text-2xl">X</p>
		{/if}
		<p class="text-xl w-10 text-center">{players}</p>
		{#if players < 10}
			<button
				class="btn btn-secondary aspect-square text-2xl"
				on:click={() => {
					players++;
				}}
			>
				{'>'}
			</button>
		{:else}
			<p class="btn aspect-square text-xl">X</p>
		{/if}
	</div>
	<button class="btn btn-primary m-2">Play</button>
</div>
