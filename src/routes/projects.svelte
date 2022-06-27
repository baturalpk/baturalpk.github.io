<script>
	import Projects from '$lib/projects/index.svelte';
</script>

<svelte:head>
	<title>baturalpk. | Projects</title>
</svelte:head>

<h1>Projects</h1>
<Projects />

<style lang="scss">
	@import '../lib/variables.scss';

	h1 {
		color: $secondary-color;
	}
</style>
