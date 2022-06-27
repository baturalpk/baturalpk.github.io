<div>
	<h1>
		<span class="intro">
			<span id="start">
				<span>hi,</span>
				<span>I am</span>
			</span>
			<span id="end"
				><span class="accent">baturalp</span
				><!-- <span id="blink1">.</span><span id="blink2">.</span> --><span id="blink3"
					>!</span
				>
			</span>
		</span>
	</h1>
	<h2>
		<span class="accent">software engineer</span> - with passion and dedication
	</h2>
	<div class="link-group">
		<h3>
			<a class="link-default" sveltekit:prefetch href="/about"
				>&#62; Learn more about me &#60;</a
			>
		</h3>
		<h3>
			<a class="link-accent" sveltekit:prefetch href="/projects"
				>&#62; See my portfolio &#60;</a
			>
		</h3>
	</div>
</div>

<style lang="scss">
	@import '../variables.scss';

	.link-group {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		margin: 4em 0 1em;
	}

	.link-group a {
		padding: 0.75em;
		border-radius: 1em;
	}

	.link-group a:hover {
		color: $primary-color;
		text-decoration: none;
	}

	.link-default {
		color: $secondary-color;
		border: 0.2em solid $secondary-color;
	}

	.link-default:hover {
		background-color: $secondary-color;
	}

	.link-accent {
		color: $accent-color;
		border: 0.2em solid $accent-color;
	}

	.link-accent:hover {
		background-color: $accent-color;
	}

	div {
		// display: flex;
		flex-direction: column;
		align-items: left;
		justify-content: space-evenly;
		max-width: 90vw;
	}

	h1 {
		color: $secondary-color;
		text-align: left;
		// font-size: 4vw;
		font-size: 7em;
	}

	h1 span.intro {
		letter-spacing: 0.1em;
	}

	h2 {
		color: $secondary-color;
		font-weight: bold;
		// font-size: 2vw;
		font-size: 3em;
	}

	h3 {
		// font-size: 1.25vw;
		font-size: 1.25em;
	}

	.accent {
		color: $accent-color;
	}

	// span#blink1 {
	// 	animation: blinkAnim infinite 1s linear;
	// }

	// span#blink2 {
	// 	animation: blinkAnim infinite 1.5s linear;
	// }

	// span#blink3 {
	// 	animation: blinkAnim infinite 2s linear;
	// }

	// @keyframes blinkAnim {
	// 	from {
	// 		opacity: 1;
	// 	}
	// 	50% {
	// 		opacity: 0;
	// 	}
	// 	to {
	// 		opacity: 1;
	// 	}
	// }

	@media only screen and (max-width: 1280px) {
		.intro {
			// display: flex;
			flex-direction: column;
			justify-content: flex-start;
			align-items: flex-start;
			min-width: 80vw;
		}

		// #start > br {
		// 	display: none;
		// }

		// .intro > #start {
		// 	font-size: 7vw;
		// }

		// .intro > #end {
		// 	font-size: 5vw;
		// }

		h1 {
			font-size: 8vw;
		}

		h2 {
			font-size: 4vw;
		}

		h3 {
			font-size: large;
		}

		div {
			flex-direction: column-reverse;
			justify-content: flex-start;
		}
	}

	@media only screen and (max-width: 768px) {
		h3 {
			font-size: 3vw;
		}

		.link-group {
			align-items: flex-start;
			flex-direction: column;
			margin: 2em 0;
			min-height: 22.5vw;
			// min-height: 30vw;
		}
	}
</style>
