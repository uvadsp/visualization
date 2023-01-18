<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { data } from '../data/cocaine_related.js';

	onMount(async () => {
		const ctx = document.getElementById('doughnut');

		const labels = data.forEach((x, i) => console.log(x));

		console.log(labels.relative);
		console.log(score);

		new Chart(ctx, {
			type: 'doughnut',
			data: {
				labels: [],
				data: []
			},
			options: {
				responsive: true,
				plugins: {
					legend: {
						position: 'top'
					},
					title: {
						display: true,
						text: 'Chart.js Doughnut Chart'
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
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 0.5em;
		background: white;
		grid-column: 1 / 7;
		grid-row: 1 / 6;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
