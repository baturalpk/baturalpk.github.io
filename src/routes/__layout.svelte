<script>
	import Contact from '$lib/contact/index.svelte';
	import Footer from '$lib/footer/index.svelte';
	import Header from '$lib/header/index.svelte';
	import '../app.scss';
</script>

<svelte:head>
	<link rel="icon" type="image/svg" href="/favicon.png" />
</svelte:head>

<Header />
<main>
	<slot />
</main>
<Contact />
<Footer />

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		/* max-width: 1024px; */
		margin: 0 auto;
		box-sizing: border-box;
	}
</style>
