<script lang="ts">
	export let stepIndex: number;
</script>

<h1>Activities for well-being and self-improvement</h1>

<ul>
	<li>at least 8000 steps a day</li>
	<li>exercise at least 4 times a week</li>
	<li>read one book every month</li>
	<li>blood test once a year</li>
	<li>meditation, journaling, yoga all day everyday</li>
	{#if stepIndex > 1}
		<li>open source contribution once or twice <em>total</em></li>
	{/if}
</ul>
