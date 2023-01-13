<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {
		const ctx = document.getElementById('Line');

		new Chart(ctx, {
			type: 'line',
			data: {
				labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul'],
				datasets: [
					{
						label: 'Google searches',
						data: [2, 6, 9, 13, 16, 21, 28],
						borderWidth: 1
					},
					{
						label: 'News articles',
						data: [2, 3, 4, 5, 6, 16, 21],
						borderWidth: 1
					},
					{
						label: 'Court cases',
						data: [2, 3, 3, 4, 5, 10, 12],
						borderWidth: 1
					}
				]
			},
			options: {
				responsive: true,
				maintainAspectRatio: false,
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
