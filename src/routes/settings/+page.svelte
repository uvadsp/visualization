<script>
	import Nav from '../../components/Nav.svelte';
	import Trends from '../../components/Downloads_trends.svelte';
	import Tweets from '../../components/Downloads_twitter.svelte';
	import News from '../../components/Downloads_news.svelte';
	import Related from '../../components/Downloads_related.svelte';
</script>

<Nav />
<main>
	<header>
		<h1>Settings</h1>
		<p>Download the raw datasets in different formats (.cvs, .json) used in the visualizations.</p>
	</header>
	<Trends />
	<Related />
	<Tweets />
	<News />
</main>

<svelte:head>
	<title>Settings - Dashboard</title>
	<link rel="icon" type="image/svg" href="/images/logo.svg" />
	<link rel="icon" href="/images/logo.png" type="image/png" />
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

	header {
		grid-column: 1 / 8;
		grid-row: 1 / 2;
		color: #3d8ad0;
	}

	p {
		color: #4b5565;
	}
</style>
