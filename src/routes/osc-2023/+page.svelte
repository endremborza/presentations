<script lang="ts">
	import OscTorso from '$lib/OscTorso.svelte';
	import { fade, fly, slide, scale, blur } from 'svelte/transition';
	import { flip } from 'svelte/animate';
	import * as eases from 'svelte/easing';
	import OscTop from '$lib/OscTop.svelte';
	import GeneralFoot from '$lib/GeneralFoot.svelte';
	import type { SvelteComponent } from 'svelte';

	import stepIndices from '$lib/osc-slides/slinds.json';

	let bgIndex = 0;

	$: stepIndex = stepIndices[bgIndex];
	let stepCount = stepIndices.length - 1;

	let duration = 700;

	function onKeyDown(event: KeyboardEvent) {
		console.log(bgIndex);
		switch (event.key) {
			case ' ':
			case 'ArrowRight':
				bgIndex = Math.min(stepCount, bgIndex + 1);
				break;
			case 'ArrowLeft':
				bgIndex = Math.max(0, bgIndex - 1);
				break;
		}
	}

	const baseComps = {
		top: OscTop,
		torso: OscTorso,
		foot: GeneralFoot
	};

	let components: { top: SvelteComponent; torso?: SvelteComponent; foot: SvelteComponent };

	$: {
		if (stepIndex < 1) {
			components = { top: baseComps.top, foot: baseComps.foot };
		} else {
			components = baseComps;
		}
	}
</script>

<svelte:head>
	<title>Open Source Meetup 2023</title>
</svelte:head>

<svelte:window on:keydown={onKeyDown} />

<prez>
	{#each Object.entries(components) as [name, elem] (name)}
		<div
			in:scale={{ easing: eases.sineIn, duration }}
			out:scale={{ easing: eases.sineOut, duration }}
			animate:flip={{ duration }}
		>
			<svelte:component this={elem} {stepIndex} {stepIndices} />
		</div>
	{/each}
</prez>

<style>
	div {
		display: flex;
		justify-content: center;
	}

	prez {
		display: flex;
		height: 100vh;
		justify-content: space-evenly;
		align-items: stretch;
		flex-direction: column;
	}
</style>
