<script>
	import svelteIcon from './svelte-logo.svg';
	let year = new Date().getFullYear();
</script>

<footer>
	<hr />
	<p>
		<b><a href="https://www.linkedin.com/in/baturalpkiziltan">LinkedIn</a></b>
		&nbsp;&nbsp;&nbsp;
		<b><a href="https://github.com/baturalpk">GitHub</a></b>
	</p>
	<p>
		Built with &nbsp;<a target="_blank" href="https://svelte.dev"
			><img src={svelteIcon} alt="Svelte" />velte</a
		>&nbsp; and &nbsp;💖. <br />Source code can be found
		<a target="_blank" href="https://github.com/baturalpk/baturalpk.github.io/tree/develop"
			><b>here</b></a
		>.
	</p>
	<p>© {year} BATURALP KIZILTAN</p>
</footer>

<style lang="scss">
	footer {
		text-align: center;
	}

	footer img {
		max-height: 1.5rem;
	}

	footer p br {
		display: none;
	}

	@media only screen and (max-width: 768px) {
		footer p br {
			display: block;
		}
	}
</style>
