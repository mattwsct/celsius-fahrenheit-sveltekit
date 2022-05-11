<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	import Counter from '$lib/Counter.svelte';
</script>

<svelte:head>
	<title>Celcius/fahrenheit converter</title>
	<meta name="description" content="Celcius/fahrenheit converter made in SvelteKit" />
</svelte:head>

<section>
	<h1>Celcius/fahrenheit converter made with SvelteKit</h1>

	<h2>Try incrementing or decrementing the below values to see the results change.</h2>

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

	h1 {
		width: 100%;
	}
</style>
