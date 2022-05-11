<script lang="ts">
	import { spring } from 'svelte/motion';

	let count_celcius = 24;
	let count_fahrenheit = 75;

	const displayed_count_celcius = spring();
	$: displayed_count_celcius.set(count_celcius);
	$: offset_celcius = modulo($displayed_count_celcius, 1);

	const displayed_count_fahrenheit = spring();
	$: displayed_count_fahrenheit.set(count_fahrenheit);
	$: offset_fahrenheit = modulo($displayed_count_fahrenheit, 1);

	function modulo(n: number, m: number) {
		// handle negative numbers
		return ((n % m) + m) % m;
	}

	function increment_celcius() {
		count_celcius++;
		celcius_to_fahrenheit(count_celcius);
	}

	function decrement_celcius() {
		count_celcius--;
		celcius_to_fahrenheit(count_celcius);
	}

	function increment_fahrenheit() {
		count_fahrenheit++;
		fahrenheit_to_celcius(count_fahrenheit);
	}

	function decrement_fahrenheit() {
		count_fahrenheit--;
		fahrenheit_to_celcius(count_fahrenheit);
	}

	function celcius_to_fahrenheit(celcius: number) {
		count_fahrenheit = Math.round(celcius * 1.8 + 32);
		return count_fahrenheit;
	}

	function fahrenheit_to_celcius(fahrenheit: number) {
		count_celcius = Math.round((fahrenheit - 32) / 1.8);
		return count_celcius;
	}

</script>

<div class="counter celcius">
	<button on:click={decrement_celcius} aria-label="Decrease the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5" />
		</svg>
	</button>

	<div class="counter-viewport">
		<div class="counter-digits" style="transform: translate(0, {100 * offset_celcius}%)">
			<strong class="hidden" aria-hidden="true">{Math.floor($displayed_count_celcius + 1)}</strong>
			<strong>{Math.floor($displayed_count_celcius)}</strong>
		</div>
	</div>

	<button on:click={increment_celcius} aria-label="Increase the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
		</svg>
	</button>
</div>

<div class="counter fahrenheit">
	<button on:click={decrement_fahrenheit} aria-label="Decrease the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5" />
		</svg>
	</button>

	<div class="counter-viewport">
		<div class="counter-digits" style="transform: translate(0, {100 * offset_fahrenheit}%)">
			<strong class="hidden" aria-hidden="true">{Math.floor($displayed_count_fahrenheit + 1)}</strong>
			<strong>{Math.floor($displayed_count_fahrenheit)}</strong>
		</div>
	</div>

	<button on:click={increment_fahrenheit} aria-label="Increase the counter by one">
		<svg aria-hidden="true" viewBox="0 0 1 1">
			<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
		</svg>
	</button>
</div>

<style>
	.counter {
		display: flex;
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
	}

	.counter button {
		width: 2em;
		padding: 0;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 0;
		background-color: transparent;
		touch-action: manipulation;
		color: var(--text-color);
		font-size: 2rem;
	}

	.counter button:hover {
		background-color: var(--secondary-color);
	}

	svg {
		width: 25%;
		height: 25%;
	}

	path {
		vector-effect: non-scaling-stroke;
		stroke-width: 2px;
		stroke: var(--text-color);
	}

	.counter-viewport {
		width: 8em;
		height: 4em;
		overflow: hidden;
		text-align: center;
		position: relative;
	}

	.counter-viewport strong {
		position: absolute;
		display: flex;
		width: 100%;
		height: 100%;
		font-weight: 400;
		color: var(--accent-color);
		font-size: 4rem;
		align-items: center;
		justify-content: center;
	}

	.counter-digits {
		position: absolute;
		width: 100%;
		height: 100%;
	}

	.hidden {
		top: -100%;
		user-select: none;
	}
</style>
