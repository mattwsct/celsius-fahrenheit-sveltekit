<script lang="ts">
	let count_celsius = 24;
	let count_fahrenheit = 75.2;

	const min_celsius = -573;
	const max_celsius = 537;

	const min_fahrenheit = -999;
	const max_fahrenheit = 999;

	let increment_celsius = () => {
		if (count_celsius < max_celsius) {
			count_celsius = Math.round(count_celsius + 1);
			update_celsius();
		}
	};

	let decrement_celsius = () => {
		if (count_celsius > min_celsius) {
			count_celsius = Math.round(count_celsius - 1);
			update_celsius();
		}
	};

	let increment_fahrenheit = () => {
		if (count_fahrenheit < max_fahrenheit) {
			count_fahrenheit = Math.round(count_fahrenheit + 1);
			update_fahrenheit();
		}
	};

	let decrement_fahrenheit = () => {
		if (count_fahrenheit > min_fahrenheit) {
			count_fahrenheit = Math.round(count_fahrenheit - 1);
			update_fahrenheit();
		}
	};

	let update_celsius = () => {
		if (count_celsius > max_celsius) {
			count_celsius = max_celsius;
		} else if (count_celsius < min_celsius) {
			count_celsius = min_celsius;
		}
		count_fahrenheit = Math.round((count_celsius * 1.8 + 32) * 10) / 10;
	};

	let update_fahrenheit = () => {
		if (count_fahrenheit > max_fahrenheit) {
			count_fahrenheit = max_fahrenheit;
		} else if (count_fahrenheit < min_fahrenheit) {
			count_fahrenheit = min_fahrenheit;
		}
		count_celsius = Math.round(((count_fahrenheit - 32) / 1.8) * 10) / 10;
	};

	let round_numbers = () => {
		count_celsius = Math.round(count_celsius * 10) / 10;
		count_fahrenheit = Math.round(count_fahrenheit * 10) / 10;
	};
</script>

<h1>Temperature Conversion</h1>
<div class="counter-container">
	<div class="celsius">
		<h2>Celsius (ºC)</h2>
		<div class="counter">
			<button on:click={decrement_celsius} aria-label="Decrease the counter by one">
				<svg aria-hidden="true" viewBox="0 0 1 1">
					<path d="M0,0.5 L1,0.5" />
				</svg>
			</button>
			<input
				class="temperature-input"
				type="number"
				bind:value={count_celsius}
				on:input={update_celsius}
				on:change={round_numbers}
			/>

			<button on:click={increment_celsius} aria-label="Increase the counter by one">
				<svg aria-hidden="true" viewBox="0 0 1 1">
					<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
				</svg>
			</button>
		</div>
	</div>

	<div class="fahrenheit">
		<h2>Fahrenheit (ºF)</h2>
		<div class="counter">
			<button on:click={decrement_fahrenheit} aria-label="Decrease the counter by one">
				<svg aria-hidden="true" viewBox="0 0 1 1">
					<path d="M0,0.5 L1,0.5" />
				</svg>
			</button>
			<input
				class="temperature-input"
				type="number"
				bind:value={count_fahrenheit}
				on:input={update_fahrenheit}
				on:change={round_numbers}
			/>

			<button on:click={increment_fahrenheit} aria-label="Increase the counter by one">
				<svg aria-hidden="true" viewBox="0 0 1 1">
					<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
				</svg>
			</button>
		</div>
	</div>
</div>
<div class="about">
	<h2>About this app</h2>

	<p>
		This is a <a href="https://kit.svelte.dev">SvelteKit</a> app that converts celsius and fahrenheit.
	</p>
	<p>
		Initially I had intented to create the app with vanilla JavaScript, but I'd been interested in
		Svelte and SvelteKit for some time and wanted to try it out.
	</p>
	<p>
		I love how lightweight Svelte is, how it compiles down to pure JavaScript without all the bulk
		of a virtual DOM.
	</p>
</div>

<style>
	.counter-container {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
	}
	.counter-container > div {
		max-width: 320px;
		background: #ffffff33;
		border-radius: 10px;
		margin: 10px 10px;
		min-height: 170px;
	}
	.about {
		margin: 50px auto 0 auto;
		max-width: 720px;
	}
	h2 {
		font-size: 2rem;
		text-align: center;
	}
	.counter {
		display: flex;
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem auto;
		justify-content: center;
	}

	.temperature-input {
		width: 60%;
		position: inherit;
		text-align: center;
		color: var(--accent-color);
		font-size: 3rem;
		border: none;
		background-color: transparent;
		outline: none;
		-moz-appearance: textfield;
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
		stroke: var(--complementary-color);
	}
</style>
