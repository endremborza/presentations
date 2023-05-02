<script lang="ts">
	export let stepIndex: number;
	export let stepIndices: number[];
</script>

<top>
	<h1 class={stepIndex > 0 ? '' : 'prelarge'}>
		Exploring the Overwhelming Benefits of an Open Source Contribution in a Way that Might Motivate
		You to Actually Make <span
			class={stepIndex < stepIndices[stepIndices.length - 1] ? '' : 'fin-emph'}>One</span
		>
	</h1>
</top>

<style>
	top {
		display: flex;
		flex: 3;
		max-width: 94rem;
		padding-left: 3rem;
		padding-right: 3rem;
	}

	span,
	h1 {
		transition: all 0.8s ease;
	}

	.prelarge {
		font-size: 4.5em;
	}

	.fin-emph {
		font-size: 1.5em;
		/* text-decoration: underline; */
		color: var(--color-theme-2);
	}
</style>
