<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	import Counter from '$lib/Counter.svelte';
</script>

<svelte:head>
	<title>Celsius/fahrenheit converter</title>
	<meta name="description" content="Celsius/fahrenheit converter made in SvelteKit" />
</svelte:head>

<section>
	<Counter />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
		margin: var(--column-margin-top) auto 0 auto;
	}
</style>
