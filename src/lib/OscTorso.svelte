<script lang="ts">
	import ContentsBar from './ContentsBar.svelte';

	import oscToc from '$lib/osc-slides/side-content.json';
	import SlideContent from './osc-slides/SlideContent.svelte';

	export let stepIndex = 1;
	export let stepCount = 0;
</script>

<torso
	><div class="contents"><ContentsBar contents={oscToc} {stepIndex} /></div>
	<div class="current-slide">
		<SlideContent {stepIndex} />
	</div></torso
>

<style>
	div {
		border: 0.3rem;
		border-style: solid;
		border-radius: 1rem;
		border-color: var(--color-theme-1);
		box-shadow: 0px 0px 4px 4px var(--color-theme-2);
		padding: 1rem;
		margin: 0.5rem;
	}

	.contents {
		flex: 1;
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
	}

	.current-slide {
		flex: 3;
		font-size: xx-large;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	torso {
		height: 55vh;
		width: 100%;
		flex: 4;
		display: flex;
		max-width: 120rem;
		justify-items: stretch;
		align-items: stretch;
	}
</style>
