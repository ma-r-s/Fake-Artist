<script>
	import { playersStore, colors, mostVotedStore } from '$lib/stores.js';
	let currPlayer = 0;
	let votes = Array($playersStore).fill(0);
	const vote = (i) => {
		if (currPlayer < $playersStore) {
			votes[i]++;
			currPlayer++;
		}
		if (currPlayer == $playersStore) {
			mostVotedStore.set(votes.indexOf(Math.max(...votes)));
		}
	};
	const mostVoted = () => {};
</script>

<div class="flex justify-evenly flex-col items-center min-h-screen text-2xl font-bold">
	<p class="text-4xl">
		{#if currPlayer < $playersStore}
			Player
			{currPlayer + 1} vote
		{:else}
			Player votes
		{/if}
	</p>
	<div class="grid grid-cols-2 gap-x-10 gap-y-6">
		{#each Array($playersStore) as _, i}
			<div class="indicator">
				<span class="indicator-item badge text-black" style={`background-color: ${$colors[i]};`}
					>{votes[i]}</span
				>
				<button
					class={`btn `}
					on:click={() => {
						vote(i);
					}}
				>
					Player {i + 1}
				</button>
			</div>
		{/each}
	</div>
	{#if currPlayer == $playersStore}
		<a
			href="./reveal"
			class="btn btn-primary"
			on:click={() => {
				mostVoted;
			}}>Reveal</a
		>
	{/if}
</div>
