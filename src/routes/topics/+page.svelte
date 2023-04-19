<script>
	import ArrowBackRounded from 'virtual:icons/material-symbols/arrow-back-rounded';
	import { onMount } from 'svelte';
	import { selectedObjectStore } from '$lib/stores.js';

	let topics = [];

	onMount(() => {
		import('./topics.js').then((module) => {
			topics = module.default;
		});
	});
</script>

<a href="./" class="flex items-center gap-2">
	<ArrowBackRounded class="w-8 h-8" />
	<p class="text-xl">Back</p>
</a>
<div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4 m-3">
	{#each topics as topic}
		<a
			on:click={() => {
				//Set the selected topic to a random object from the topic
				selectedObjectStore.set(topic.objects[Math.floor(Math.random() * topic.objects.length)]);
			}}
			href="/show"
			class="btn btn-primary">{topic.name}</a
		>
	{/each}
</div>
