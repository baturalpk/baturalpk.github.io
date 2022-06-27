<script>
	export let project;
</script>

<div class="wrapper">
	<p class="project-info-title"><b>{project.title}</b></p>
	<div class="project-card">
		<div class="project-info">
			<p>{project.description}</p>
			<p><b>Tech stack: </b>{project.tech}</p>
			{#each project.external_links ?? [] as link}
				<p>
					<b
						><a target="_blank" href={link.value} class="project-sub-info-links"
							>{link.key}</a
						></b
					>
				</p>
			{/each}
		</div>
		<!-- <span>&#62;</span> -->
	</div>
</div>

<style lang="scss">
	@import '../variables.scss';

	.wrapper {
		margin: 0 2.5%;
	}

	.project-card {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: space-between;
		align-items: flex-start;
		border: 2px solid $secondary-color;
		border-radius: 1em;
		padding: 0 1.5em;
		transition: all 0.2s ease-in-out;
		min-height: 60%;
	}

	// .project-card:hover {
	// 	// cursor: pointer;
	// 	transform: scale(1.05);
	// }

	.project-card p {
		color: $secondary-color;
	}

	.project-card,
	.project-info {
		max-width: 90%;
	}

	.project-info p {
		word-wrap: break-word;
		hyphens: auto;
	}

	.project-info-title {
		font-size: larger;
		padding-left: 0.4em;
	}
</style>
