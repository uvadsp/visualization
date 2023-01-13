<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { peaks } from '../data/only_peaks_2018_2022';

	console.log(peaks);

	onMount(async () => {
		const ctx = document.getElementById('Line');

		new Chart(ctx, {
			type: 'line',
			data: {
				datasets: [
					{
						label: 'Google Trends',
						data: peaks
					}
				]
			},
			options: {
				responsive: true,
				maintainAspectRatio: false,
				scales: {
					type: 'category',
					y: {
						beginAtZero: true
					}
				},
				parsing: {
					xAxisKey: 'date',
					yAxisKey: 'cocaine'
				}
			}
		});
	});
</script>

<article>
	<h3>Interest over time</h3>
	<div class="container">
		<canvas id="Line" />
	</div>
</article>

<style>
	h3 {
		font-weight: 500;
		color: #1433dd;
	}
	.container {
		width: 100%;
		height: 100%;
	}
	article {
		padding: 0em 2em 2em 2em;
		display: flex;
		color: #3a365f;
		flex-direction: column;
		align-items: flex-start;
		border-radius: 0.5em;
		background: white;
		grid-column: 1 / 7;
		grid-row: 1 / 6;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
