<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { data } from '../data/multitimeline';

	console.log(data);

	const labels = [];
	const cleaning = data.forEach((x, i) => labels.push(x.week));
	console.log(labels);

	onMount(async () => {
		const ctx = document.getElementById('multiline');

		new Chart(ctx, {
			type: 'line',
			data: {
				labels: labels,
				datasets: [
					{
						label: 'Cocaine',
						data: data,
						parsing: {
							yAxisKey: 'cocaine'
						}
					},
					{
						label: 'GHB',
						data: data,
						parsing: {
							yAxisKey: 'ghb'
						}
					},
					{
						label: 'XTC',
						data: data,
						parsing: {
							yAxisKey: 'xtc'
						}
					}
				]
			},
			options: {
				responsive: true,
				maintainAspectRatio: false,
				scales: {
					x: {
						title: {
							display: true,
							text: 'Weeknumbers'
						}
					},
					y: {
						title: {
							display: true,
							text: 'Relative score'
						}
					}
				},
				parsing: {
					xAxisKey: 'week'
				}
			}
		});
	});
</script>

<article>
	<h3>Relative number of searches for drug keywords</h3>
	<div class="container">
		<canvas id="multiline" />
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
		grid-row: 1 / 5;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
