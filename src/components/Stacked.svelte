<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {
		const ctx = document.getElementById('stacked');

		new Chart(ctx, {
			type: 'bar',
			data: data,
			options: {
				plugins: {
					title: {
						display: true,
						text: 'Chart.js Bar Chart - Stacked'
					}
				},
				responsive: true,
				interaction: {
					intersect: false
				},
				scales: {
					x: {
						stacked: true
					},
					y: {
						stacked: true
					}
				}
			}
		});
	});
</script>

<article>
	<h3>Distribution of sources per month</h3>
	<div class="container">
		<canvas id="stacked" />
	</div>
</article>

<style>
	h2 {
		color: blue;
	}

	article {
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 0.2em;
		background: white;
		grid-column: 2 / 5;
		grid-row: 6 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
