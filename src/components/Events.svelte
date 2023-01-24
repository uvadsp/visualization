<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {});
</script>

<article>
	<ul>
		<li><span style="background-color: rgba(253, 186, 116, 1);" />Kings Day</li>
		<li><span style="background-color: rgba(126, 212, 171, 1);" />Lowlands</li>
		<li><span style="background-color: rgba(252, 237, 79, 1);" />Zwarte Cross</li>
		<li><span style="background-color: rgba(116, 62, 228, 1);" />Pride Adam</li>
		<li><span style="background-color: rgba(221, 82, 76, 1);" />Christmas</li>
		<li><span style="background-color: rgba(233, 162, 59, 1)" />New Year's Eve</li>
	</ul>
</article>

<style>
	ul li span {
		width: 0.5em;
		height: 0.5em;
		background: orange;
		border-radius: 100%;
		display: inline-block;
		margin-right: 1em;
	}

	ul {
		list-style-type: none;
		margin: 0;
		padding: 0;
	}

	ul li {
		font-size: 0.8em;
	}

	article {
		padding: 2em;
		border-radius: 0.2em;
		background: white;
		grid-column: 1 / 2;
		grid-row: 6 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
