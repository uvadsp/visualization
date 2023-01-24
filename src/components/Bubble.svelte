<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {
		const ctx = document.getElementById('bubble');

		new Chart(ctx, {
			type: 'bar',
			data: {
				labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
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
	<canvas id="bubble" />
</article>

<style>
	article {
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 0.5em;
		background: white;
		grid-column: 5 / 8;
		grid-row: 2 / 6;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
