<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {
		const ctx = document.getElementById('Line');

		new Chart(ctx, {
			type: 'line',
			data: {
				labels: ['Red', 'Blue', 'Yellow', 'Green'],
				datasets: [
					{
						label: '# of Votes',
						data: [12, 19, 3, 5, 2, 3],
						borderWidth: 1
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
	<canvas id="Line" />
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
