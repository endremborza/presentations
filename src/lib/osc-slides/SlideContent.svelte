
<script lang="ts">
	import OscSlide1 from './OscSlide1.svelte';
	import OscSlide2 from './OscSlide2.svelte';
	import OscSlide3 from './OscSlide3.svelte';
	import OscSlide4 from './OscSlide4.svelte';
	import OscSlide5 from './OscSlide5.svelte';
	import OscSlide6 from './OscSlide6.svelte';
	import OscSlide7 from './OscSlide7.svelte';
	import OscSlide8 from './OscSlide8.svelte';
	import OscSlide9 from './OscSlide9.svelte';

	export let stepIndex: number;

	const components = [OscSlide1, OscSlide2, OscSlide3, OscSlide4, OscSlide5, OscSlide6, OscSlide7, OscSlide8, OscSlide9];

	function getCurrent(ind: number) {
		for (let i = 1; i <= components.length; i++) {
			if (i + 1 > ind) {
				return components[i-1];
			}
		}
	}

	$: currentComponent = getCurrent(stepIndex);
</script>

<svelte:component this={currentComponent} {stepIndex} />

