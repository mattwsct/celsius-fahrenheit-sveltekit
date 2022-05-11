<script lang="ts">
	let count_celcius = 24;
	let count_fahrenheit = 75;

	let increment_celcius = () => {
		count_celcius++;
		update_celcius();
	};

	let decrement_celcius = () => {
		count_celcius--;
		update_celcius();
	};

	let increment_fahrenheit = () => {
		count_fahrenheit++;
		update_fahrenheit();
	};

	let decrement_fahrenheit = () => {
		count_fahrenheit--;
		update_fahrenheit();
	};

	let celcius_to_fahrenheit = () => {
		count_fahrenheit = Math.round(count_celcius * 1.8 + 32);
	};

	let fahrenheit_to_celcius = () => {
		count_celcius = Math.round((count_fahrenheit - 32) / 1.8);
	};

	let update_celcius = () => {
		if (count_celcius > 10000) {
			count_celcius = 10000;
		} else if (count_celcius < -10000) {
			count_celcius = -10000;
		}
		celcius_to_fahrenheit();
	};
	let update_fahrenheit = () => {
		if (count_fahrenheit > 10000) {
			count_fahrenheit = 10000;
		} else if (count_fahrenheit < -10000) {
			count_fahrenheit = -10000;
		}
		fahrenheit_to_celcius();
	};
</script>

<div class="celcius">
	<h1>Celcius</h1>
	<div class="counter">
		<button on:click={decrement_celcius} aria-label="Decrease the counter by one">
			<svg aria-hidden="true" viewBox="0 0 1 1">
				<path d="M0,0.5 L1,0.5" />
			</svg>
		</button>

		<div class="counter-viewport">
			<input
				class="temperature-input"
				type="number"
				bind:value={count_celcius}
				on:input={update_celcius}
			/>
		</div>

		<button on:click={increment_celcius} aria-label="Increase the counter by one">
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
		width: inherit;
		border: none;
		background-color: transparent;
		text-align: center;
		color: var(--accent-color);
		font-size: 4rem;
		-webkit-appearance: none;
		border: none;
		background-color: transparent;
		resize: none;
		outline: none;
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
		width: 14em;
		min-height: 4em;
		overflow: hidden;
		text-align: center;
		position: relative;
	}
</style>
