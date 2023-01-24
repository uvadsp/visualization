<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {
		const ctx = document.getElementById('pie');

		const doughnut = new Chart(ctx, {
			type: 'doughnut',
			data: {
				labels: ['Tweets', 'Trends', 'News'],
				datasets: [
					{
						label: 'Dataset 1',
						data: [19, 21, 50]
					}
				]
			},
			options: {
				responsive: true,
				maintainAspectRatio: false
			}
		});
		doughnut.height = 100;
	});
</script>

<article>
	<h3>Distribution of sources per year</h3>
	<div class="container">
		<canvas id="pie" />
	</div>
</article>

<style>
	h3 {
		color: blue;
		font-weight: 500;
	}

	.container {
		width: 100%;
		height: 80%;
	}

	article {
		display: flex;
		padding: 0em 2em 2em 2em;
		flex-direction: column;
		border-radius: 0.2em;
		background: white;
		grid-column: 6 / 7;
		grid-row: 6 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
