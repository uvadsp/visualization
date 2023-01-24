<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {
		const ctx = document.getElementById('stacked');

		new Chart(ctx, {
			type: 'bar',
			data: {
				labels: [
					'Jan',
					'Feb',
					'Mar',
					'Apr',
					'May',
					'Jun',
					'Jun',
					'Aug',
					'Sep',
					'Okt',
					'Nov',
					'Dec'
				],
				datasets: [
					{
						label: 'Tweets',
						data: [10, 12, 45, 37, 30, 50, 80, 100, 12, 34, 45, 37],
						backgroundColor: '#5baeec',
						borderColor: '#5baeec'
					},
					{
						label: 'News',
						data: [10, 12, 45, 37, 30, 50, 80, 100, 12, 34, 45, 37],
						backgroundColor: '#ed6d85',
						borderColor: '#ed6d85'
					},
					{
						label: 'Trends',
						data: [10, 12, 45, 37, 30, 50, 80, 100, 12, 34, 45, 37],
						backgroundColor: '#eab83f',
						borderColor: '#eab83f'
					}
				]
			},
			options: {
				responsive: true,
				maintainAspectRatio: false,
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
	h3 {
		color: blue;
		font-weight: 500;
	}

	.container {
		width: 100%;
		height: 100%;
	}

	article {
		display: flex;
		padding: 0em 2em 2em 2em;
		flex-direction: column;
		border-radius: 0.2em;
		background: white;
		grid-column: 2 / 6;
		grid-row: 6 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
