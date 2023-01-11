<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {
		const ctx = document.getElementById('doughnut');

		new Chart(ctx, {
			type: 'doughnut',
			data: {
				labels: ['Red', 'Blue', 'Yellow'],
				datasets: [
					{
						label: 'My First Dataset',
						data: [300, 50, 100],
						backgroundColor: ['rgb(255, 99, 132)', 'rgb(54, 162, 235)', 'rgb(255, 205, 86)'],
						hoverOffset: 4
					}
				]
			},
			options: {
				scales: {
					y: {
						beginAtZero: true
					}
				}
			}
		});
	});
</script>

<article>
	<canvas id="doughnut" />
</article>

<style>
	article {
		border-radius: 0.5em;
		background: white;
		grid-column: 1 / 2;
		grid-row: 6 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
