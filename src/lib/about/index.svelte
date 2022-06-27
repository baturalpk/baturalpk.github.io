<script>
	import { fly } from 'svelte/transition';

	const msInAYear = 3.156 * Math.pow(10, 10);
	let age = Math.floor((new Date().valueOf() - new Date(2001, 5).valueOf()) / msInAYear);

	let failedToFetch = false;
	async function FetchTechStack() {
		try {
			const res = await fetch('/data/tech_stack.json');
			const data = await res.json();
			return data;
		} catch (err) {
			failedToFetch = true;
		}
	}
</script>

<div id="about">
	<div id="wrapper">
		<p class="paragraph">
			Hello! I am Baturalp KIZILTAN, {age} y/o software developer, currently pursuing a bachelor's
			degree in Computer Engineering as a senior year student.
		</p>
		<p class="paragraph">
			For the last year, I have primarily worked on server-side technologies, designed and
			implemented web backends/APIs. On the side, I build frontendy things,
			<i>like this website^^</i>, occasionally.
		</p>
		<br />
		<h2>Technologies</h2>
		{#await FetchTechStack()}
			{#if failedToFetch}
				<p class="error" on:click={() => location.reload()}>
					Couldn't fetch the technologies.<br />Please try to reload the page :(
				</p>
			{:else}
				<h2 class="message">...</h2>
			{/if}
		{:then techStack}
			<p>Here are some technologies I have been working with recently:</p>
			<ul in:fly={{ x: -300, duration: 1500 }}>
				{#each techStack as tech}
					<li>{tech}</li>
				{/each}
				<li>... and more</li>
			</ul>
			<p in:fly={{ y: 200, duration: 1500 }}>
				Besides them, I am not a fan of particular technologies and have always supported
				the idea of picking right tools for building the right product. Therefore, if
				needed, I can always grasp new concepts, libraries, languages, or whatsoever
				quickly.
			</p>
		{/await}
	</div>
</div>

<style lang="scss">
	@import '../variables.scss';

	#about {
		display: flex;
		justify-content: center;
	}

	#wrapper {
		text-align: left;
		max-width: 50vw;
	}

	h2 {
		font-size: x-large;
		font-weight: bolder;
		letter-spacing: 3px;
	}

	p {
		word-wrap: break-word;
		hyphens: none;
		line-height: 2em;
	}

	p.paragraph::first-letter {
		text-transform: uppercase;
		font-size: 1.5em;
		font-weight: bold;
	}

	p.error {
		color: $accent-color;
	}

	p.error:hover {
		text-decoration: underline;
	}

	ul {
		display: grid;
		grid-template-columns: repeat(2, minmax(0, 1fr));
		gap: 1em 0;
	}

	li::before {
		content: '> ';
		position: absolute;
		transform: translateX(-1.5em);
		color: $accent-color;
		font-weight: bold;
	}

	li {
		font-family: 'OpenSansItalic';
		list-style-type: none;
		line-height: 1.75em;
	}

	@media only screen and (max-width: 1280px) {
		#wrapper {
			max-width: 75vw;
		}
	}

	@media only screen and (max-width: 768px) {
		h2 {
			font-size: large;
		}

		p {
			font-size: small;
		}

		li::before {
			transform: translateX(-2em);
		}

		li {
			font-size: small;
		}
	}
</style>
