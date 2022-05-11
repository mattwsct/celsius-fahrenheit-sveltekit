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
		} else if (!(count_celsius > min_celsius && count_celsius < max_celsius)) {
			count_celsius = Math.round(count_celsius * 10) / 10;
		}
		count_fahrenheit = Math.round((count_celsius * 1.8 + 32) * 10) / 10;
	};

	let update_fahrenheit = () => {
		if (count_fahrenheit > max_fahrenheit) {
			count_fahrenheit = max_fahrenheit;
		} else if (count_fahrenheit < min_fahrenheit) {
			count_fahrenheit = min_fahrenheit;
		} else if (!(count_fahrenheit > min_fahrenheit && count_fahrenheit < max_fahrenheit)) {
			count_fahrenheit = Math.round(count_fahrenheit * 10) / 10;
		}
		count_celsius = Math.round(((count_fahrenheit - 32) / 1.8) * 10) / 10;
	};

	let round_numbers = () => {
		count_celsius = Math.round(count_celsius * 10) / 10;
		count_fahrenheit = Math.round(count_fahrenheit * 10) / 10;
	};
</script>

<div class="celsius">
	<h1>Celsius</h1>
	<div class="counter">
		<button on:click={decrement_celsius} aria-label="Decrease the counter by one">
			<svg aria-hidden="true" viewBox="0 0 1 1">
				<path d="M0,0.5 L1,0.5" />
			</svg>
		</button>

		<div class="counter-viewport">
			<input
				class="temperature-input"
				type="number"
				bind:value={count_celsius}
				on:input={update_celsius}
				on:change={round_numbers}
			/>
		</div>

		<button on:click={increment_celsius} aria-label="Increase the counter by one">
			<svg aria-hidden="true" viewBox="0 0 1 1">
				<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
			</svg>
		</button>
	</div>
</div>

<div class="fahrenheit">
	<h1>Fahrenheit</h1>
	<div class="counter">
		<button on:click={decrement_fahrenheit} aria-label="Decrease the counter by one">
			<svg aria-hidden="true" viewBox="0 0 1 1">
				<path d="M0,0.5 L1,0.5" />
			</svg>
		</button>

		<div class="counter-viewport">
			<input
				class="temperature-input"
				type="number"
				bind:value={count_fahrenheit}
				on:input={update_fahrenheit}
				on:change={round_numbers}
			/>
		</div>

		<button on:click={increment_fahrenheit} aria-label="Increase the counter by one">
			<svg aria-hidden="true" viewBox="0 0 1 1">
				<path d="M0,0.5 L1,0.5 M0.5,0 L0.5,1" />
			</svg>
		</button>
	</div>
</div>

<style>
	.counter {
		display: flex;
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
	}

	.temperature-input {
		width: 200px;
		position: inherit;
		text-align: center;
		color: var(--accent-color);
		font-size: 4rem;
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

	.counter-viewport {
		min-height: 4em;
		overflow: hidden;
	}
</style>
