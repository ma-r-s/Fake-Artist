<script>
	import { onMount } from 'svelte';
	import ArrowBackRounded from 'virtual:icons/material-symbols/arrow-back-rounded';
	import { selectedObjectStore, fakeArtistStore, playersStore } from '$lib/stores.js';
	let currPlayer = 0;
	let show = false;
	let selectedObject;
	let fakeArtist;
	let numPlayers;
	onMount(() => {
		selectedObjectStore.subscribe((value) => {
			selectedObject = value;
		});
		fakeArtistStore.subscribe((value) => {
			fakeArtist = value;
		});
		playersStore.subscribe((value) => {
			numPlayers = value;
		});
	});
</script>

<a href="./topics" class="flex items-center gap-2 absolute">
	<ArrowBackRounded class="w-8 h-8" />
	<p class="text-xl">Back</p>
</a>
<div class="flex flex-col items-center justify-center min-h-screen">
	<p class="font-bold text-3xl">Player {currPlayer + 1}</p>

	{#if show}
		{#if currPlayer == fakeArtist}
			<p class="text-2xl">You are the FAKE artist!</p>
		{:else}
			<p class="text-2xl">You are a REAL artist!</p>
			<p class="text-2xl">Draw: {selectedObject}</p>
		{/if}
		{#if currPlayer < numPlayers - 1}
			<button
				on:click={() => {
					show = !show;
					currPlayer++;
				}}
				class="btn btn-secondary m-4">Next player</button
			>
		{:else}
			<a href="/draw" class="btn m-4">Start game!</a>
		{/if}
	{:else}
		<button
			on:click={() => {
				show = !show;
			}}
			class="btn btn-primary m-4">Show me!</button
		>
	{/if}
</div>
