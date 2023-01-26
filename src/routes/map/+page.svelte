<script>
	import { onMount } from 'svelte';
	import Nav from '../../components/Nav.svelte';
	import Line from '../../components/Line.svelte';
	import Map from '../../components/Map.svelte';
</script>

<Nav />
<main>
	<Map />
</main>

<svelte:head>
	<title>Location - Dashboard</title>
	<link rel="icon" type="image/svg" href="/images/logo.svg" />
	<link rel="icon" href="/images/logo.png" type="image/png" />
	<link rel="stylesheet" href="css/nice-select2.css" />
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

	ul {
		margin: 0;
		padding: 0;
		grid-column: 1 / 7;
		grid-row: 1 / 2;
		display: flex;
		width: 100%;
		justify-content: space-between;
	}
</style>
