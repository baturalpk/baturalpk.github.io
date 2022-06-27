<script>
	import { page } from '$app/stores';
	import { fade } from 'svelte/transition';
	import CloseIcon from './icons/CloseIcon.svelte';
	import MenuIcon from './icons/MenuIcon.svelte';

	let mobileNavOpened = false;

	function tapMobileNav() {
		mobileNavOpened = !mobileNavOpened;
	}
</script>

<header>
	<div class="corner" class:active={$page.url.pathname === '/'}>
		<a sveltekit:prefetch href="/" on:click={mobileNavOpened ? tapMobileNav() : {}}>
			<img id="logo" src="/images/logo.png" alt="baturalp-logo" />
		</a>
	</div>

	<div class="menu corner" on:click={tapMobileNav}>
		<MenuIcon />
	</div>

	<nav id="default-nav">
		<ul>
			<li class:active={$page.url.pathname === '/about'}>
				<a sveltekit:prefetch href="/about">About me</a>
			</li>
			<li class:active={$page.url.pathname === '/'}>
				<a sveltekit:prefetch href="/">Home</a>
			</li>
			<li class:active={$page.url.pathname === '/projects'}>
				<a sveltekit:prefetch href="/projects">Projects</a>
			</li>
			<li>
				<a target="_blank" href="https://github.com/baturalpk">GitHub</a>
			</li>
			<li>
				<a target="_blank" href="https://www.linkedin.com/in/baturalpkiziltan/">LinkedIn</a>
			</li>
			<!-- <li>
				<a target="_blank" href="/files/Resume-Baturalp_KIZILTAN.pdf">&#62; Resume &#60;</a>
			</li> -->
		</ul>
	</nav>

	{#if mobileNavOpened == true}
		<div
			class="mobile-overlay"
			on:click={tapMobileNav}
			transition:fade={{ delay: 0, duration: 300 }}
		>
			<div class="overlay-close">
				<CloseIcon />
			</div>

			<nav class="mobile-nav">
				<ul>
					<li class:active={$page.url.pathname === '/about'}>
						<a sveltekit:prefetch href="/about">About me</a>
					</li>
					<li class:active={$page.url.pathname === '/'}>
						<a sveltekit:prefetch href="/">Home</a>
					</li>
					<li class:active={$page.url.pathname === '/projects'}>
						<a sveltekit:prefetch href="/projects">Projects</a>
					</li>
					<li>
						<a target="_blank" href="https://github.com/baturalpk">GitHub</a>
					</li>
					<li>
						<a target="_blank" href="https://www.linkedin.com/in/baturalpkiziltan/"
							>LinkedIn</a
						>
					</li>
					<!-- <li>
						<a target="_blank" href="/files/Resume-Baturalp_KIZILTAN.pdf"
							>&#62; Resume &#60;</a
						>
					</li> -->
				</ul>
			</nav>
		</div>
	{/if}
</header>

<style lang="scss">
	@import '../variables.scss';

	#logo {
		transform: rotate(-12.5deg);
	}

	header {
		font-size: 1.25em;
		display: flex;
		justify-content: space-around;
		padding-top: 1rem;
	}

	.menu {
		display: none;
	}

	.corner {
		width: 5em;
		height: 5em;
	}

	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	.corner img {
		width: 5em;
		height: 5em;
		z-index: 99;
		object-fit: contain;
	}

	nav {
		display: flex;
		justify-content: center;
		background-color: $primary-color;
	}

	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: $primary-color;
		background-size: contain;
	}

	li {
		position: relative;
		height: 100%;
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		color: $text-color-1;
		padding: 0 1em;
		font-weight: 700;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: $accent-color;
	}

	.menu,
	.overlay-close {
		cursor: pointer;
	}

	.mobile-overlay {
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		position: fixed;
		z-index: 1;
		width: 100vw;
		height: 100vh;
		background-color: $primary-color;
	}

	.overlay-close {
		position: fixed;
		top: 1rem;
		right: 1.5rem;
		z-index: 2;
	}

	.mobile-nav {
		position: absolute;
		top: 50%;
		left: 50%;
		z-index: 2;
		transform: translate(-50%, -50%);
		background-color: $primary-color;
		color: $secondary-color;
	}

	.mobile-nav ul {
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
		min-height: 50vh;
	}

	.mobile-nav li > a {
		font-size: 5vw;
	}

	// li a[target='_blank']:after {
	// 	content: ' ↗';
	// 	position: relative;
	// 	vertical-align: top;
	// 	top: -0.6em;
	// }

	@media only screen and (max-width: 1024px) {
		.menu {
			display: block;
		}

		header {
			font-size: 2.5vw;
			justify-content: space-between;
			margin: 0 2em;
		}

		#default-nav {
			display: none;
		}
	}
</style>
