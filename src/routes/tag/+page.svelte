<script>
	import Nav from '../../components/Nav.svelte';
	import Line from '../../components/Line.svelte';
	import Multiline from '../../components/Multiline.svelte';
	import DoughnutOne from '../../components/Doughnut_1.svelte';
	import DoughnutTwo from '../../components/Doughnut_2.svelte';
	import DoughnutThree from '../../components/Doughnut_3.svelte';
</script>

<Nav />
<main>
	<Multiline />
	<DoughnutOne />
	<DoughnutTwo />
	<DoughnutThree />
</main>

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
		grid-row: 1 / 5;
		display: flex;
		width: 100%;
		justify-content: space-between;
	}
</style>
