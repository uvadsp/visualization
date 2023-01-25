<script>
	import Nav from '../../components/Nav.svelte';
	import Description from '../../components/Description.svelte';
	import Chart from '../../components/Chart.svelte';
	import Events from '../../components/Events.svelte';
	import LineFilter from '../../components/Line-filter.svelte';
	import Pie from '../../components/Pie.svelte';
</script>

<Nav />
<main>
	<LineFilter />
	<Description />
	<Events />
	<Pie />
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
