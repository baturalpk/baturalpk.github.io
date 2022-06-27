<script>
	import About from '$lib/about/index.svelte';
</script>

<svelte:head>
	<title>baturalpk. | About</title>
</svelte:head>

<h1>About me</h1>
<About />

<style lang="scss">
	@import '../lib/variables.scss';

	h1 {
		color: $secondary-color;
	}
</style>
