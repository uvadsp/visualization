<script>
	import Bubble from '../components/Bubble.svelte';
	import Block from '../components/Block.svelte';
	import Bar from '../components/Bar.svelte';
	import Stats from '../components/Stats.svelte';
	import List_1 from '../components/List_1.svelte';
	import List_2 from '../components/List_2.svelte';
	import List_3 from '../components/List_3.svelte';
	import List_4 from '../components/List_4.svelte';
	import List_5 from '../components/List_5.svelte';
	import List_6 from '../components/List_6.svelte';
</script>

<main>
	<ul>
		<List_1 />
		<List_2 />
		<List_3 />
		<List_4 />
		<List_5 />
		<List_6 />
	</ul>
	<Bubble />
	<Block />
	<Stats />
	<Bar />
</main>

<style>
	main {
		width: 95vw;
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
