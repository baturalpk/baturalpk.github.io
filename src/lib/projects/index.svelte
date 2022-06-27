<script>
	import { quintOut } from 'svelte/easing';
	import { slide } from 'svelte/transition';
	import ProjectCard from './ProjectCard.svelte';

	let failedToFetch = false;
	async function FetchProjects() {
		try {
			const res = await fetch('/data/projects.json');
			const data = await res.json();
			return data;
		} catch (err) {
			failedToFetch = true;
		}
	}
</script>

<section>
	{#await FetchProjects()}
		{#if failedToFetch}
			<h2 class="message error">
				Couldn't fetch the projects. Please try to reload the page :(
			</h2>
		{:else}
			<h2 class="message">Fetching...</h2>
		{/if}
	{:then projects}
		<div class="project-group" in:slide={{ delay: 150, duration: 1000, easing: quintOut }}>
			{#each projects as project}
				<ProjectCard {project} />
			{/each}
		</div>
	{/await}
</section>

<style lang="scss">
	@import '../variables.scss';

	section {
		margin: 1.5em 0;
	}

	.message {
		text-align: center;
		font-weight: bold;
		color: $secondary-color;
	}

	.error {
		color: $accent-color;
	}

	.project-group {
		display: grid;
		grid-template-columns: repeat(3, minmax(0, 1fr));
		grid-auto-rows: minmax(15em, auto);
		gap: 2em 1em;
		margin: 0 5%;
	}

	@media only screen and (max-width: 1600px) {
		.project-group {
			grid-template-columns: repeat(2, minmax(0, 1fr));
		}
	}

	@media only screen and (max-width: 1024px) {
		.project-group {
			grid-template-columns: repeat(1, minmax(0, 1fr));
		}
	}
</style>
