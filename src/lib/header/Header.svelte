<script lang="ts">
	import logo from './svelte-logo.svg';
	import DarkMode from './DarkMode.svelte';
</script>

<header>
	<div class="corner">
		<a href="https://kit.svelte.dev">
			<img src={logo} alt="SvelteKit" />
		</a>
	</div>
	<div class="corner">
		<DarkMode />
	</div>
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
	}

	.corner {
		width: 3em;
		height: 3em;
	}

	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	.corner img {
		width: 2em;
		height: 2em;
		object-fit: contain;
	}
	:global(body) {
		background-color: var(--primary-color);
		background: linear-gradient(
			180deg,
			var(--primary-color) 0%,
			var(--secondary-color) 10.45%,
			var(--tertiary-color) 41.35%
		);
		transition: background-color 0.3s;
	}
	:global(body.dark-mode) {
		background-color: var(--secondary-color);
		background: linear-gradient(
			180deg,
			var(--primary-color-dark) 0%,
			var(--secondary-color-dark) 10.45%,
			var(--tertiary-color-dark) 41.35%
		);
	}

	a:hover {
		color: var(--accent-color);
	}
</style>
