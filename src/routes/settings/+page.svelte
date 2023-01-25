<script>
	import Nav from '../../components/Nav.svelte';
	import Trends from '../../components/Downloads_trends.svelte';
	import Tweets from '../../components/Downloads_twitter.svelte';
	import News from '../../components/Downloads_news.svelte';
</script>

<Nav />
<main>
	<h1>Settings</h1>
	<Trends />
	<Tweets />
	<News />
</main>

<svelte:head>
	<title>Popularity - Dashboard</title>
</svelte:head>

<style>
	main {
		padding: 2em 2em 2em 7em;
		width: 90vw;
		height: 91vh;
		display: grid;
		grid-template-columns: repeat(6, 1fr);
		grid-template-rows: repeat(8, 1fr);
		grid-row-gap: 2em;
		grid-column-gap: 2em;
		font-family: 'Inter', sans-serif;
	}

	h1 {
		grid-column: 1 / 8;
		grid-row: 1 / 2;
		color: #3d8ad0;
	}
</style>
