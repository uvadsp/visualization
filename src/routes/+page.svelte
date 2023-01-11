<script>
	import Nav from '../components/Nav.svelte';
	import Bubble from '../components/Bubble.svelte';
	import Block from '../components/Block.svelte';
	import Bar from '../components/Bar.svelte';
	import Stats from '../components/Stats.svelte';
	import Filter from '../components/Filter.svelte';
	import List_1 from '../components/List_1.svelte';
	import List_2 from '../components/List_2.svelte';
	import List_3 from '../components/List_3.svelte';
	import List_4 from '../components/List_4.svelte';
</script>

<Nav />
<main>
	<ul>
		<Filter />
		<List_1 />
		<List_2 />
		<List_3 />
		<List_4 />
	</ul>
	<Bubble />
	<Block />
	<Stats />
	<Bar />
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
		grid-row: 1 / 2;
		display: flex;
		width: 100%;
		justify-content: space-between;
	}
</style>
