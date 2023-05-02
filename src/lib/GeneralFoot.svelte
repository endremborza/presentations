<script lang="ts">
	export let stepIndex: number;
	export let stepIndices: number[];
</script>

<foot>
	{stepIndex} / {stepIndices[stepIndices.length - 1]}
</foot>

<style>
	foot {
		display: flex;
		justify-content: center;
		flex: 1;
		font-size: 2rem;
	}
</style>
