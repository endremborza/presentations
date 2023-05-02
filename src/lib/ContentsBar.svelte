<script lang="ts">
	import { fade, fly, slide, scale, blur } from 'svelte/transition';
	import { flip } from 'svelte/animate';
	import * as eases from 'svelte/easing';

	type ContentElem = {
		text: string;
		depth: number;
		sid: number;
	};

	export let contents: ContentElem[];
	export let stepIndex: number;

	function getDisplayedContents(stepInd: number) {
		const o: ContentElem[] = [];
		contents.forEach((c) => {
			if (stepInd > c.sid) {
				o.push(c);
			}
		});
		return o;
	}

	$: displayedContents = getDisplayedContents(stepIndex);

	export let duration = 300;
</script>

{#each displayedContents as content (content.sid)}
	<div
		animate:flip={{ duration }}
		in:fade={{ easing: eases.sineIn, duration }}
		out:fade={{ easing: eases.sineOut, duration }}
		style="margin-left: {content.depth * 1.5 + 2}rem;"
	>
		{@html content.text}
	</div>
{/each}

<style>
	div {
		font-size: larger;
		font-weight: 800;
	}
	div:before {
		content: '►';
		padding-right: 5px;
	}
</style>
