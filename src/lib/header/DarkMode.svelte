<script>
	function toggle() {
		window.document.body.classList.toggle('dark-mode');
		document.documentElement.classList.toggle('dark-mode');
	}
</script>

<button on:click={toggle} class="dark-mode-button">
	<slot />
	<div class="moon">🌛</div>
	<div class="sun">☀️</div>
</button>

<style>
	button {
		background-color: var(--secondary-color-dark);
		color: white;
		border: none;
		border-radius: 4px;
		padding: 0.5rem;
		text-transform: uppercase;
		margin-top: 10px;
		width: 2em;
		height: 2em;
		line-height: 0;
	}

	:global(body.dark-mode) button {
		background-color: transparent;
		color: white;
	}

	.dark-mode-button .moon {
		display: block;
	}
	.dark-mode-button .sun {
		display: none;
	}

	:global(body.dark-mode) .dark-mode-button .moon {
		display: none;
	}
	:global(body.dark-mode) .dark-mode-button .sun {
		display: block;
	}
</style>
