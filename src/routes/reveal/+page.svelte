<script>
	import { mostVotedStore, fakeArtistStore } from '$lib/stores.js';
</script>

<div class="flex flex-col justify-center items-center gap-4 min-h-screen">
	{#if $mostVotedStore == $fakeArtistStore}
		<p class="text-3xl text-center font-bold">Player {$mostVotedStore + 1} was the fake artist!!</p>
		<p class="text-2xl text-center">The fake artist has one last chance to guess the object</p>
	{:else}
		<p class="text-3xl text-center font-bold">
			Player {$mostVotedStore + 1} was NOT the fake artist!!
		</p>
		<p class="text-2xl text-center">The fake artist was Player {$fakeArtistStore + 1}</p>
		<p class="text-2xl text-center">Well played</p>
	{/if}
	<a class="btn btn-primary" href="./">Play Again</a>
</div>
