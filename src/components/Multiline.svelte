<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { keywords } from '../data/multitimeline';
	import { weeks } from '../data/weeks';

	console.log(keywords);

	onMount(async () => {
		const ctx = document.getElementById('multiline');

		/* Get value from Year input */
		const year = document.querySelector('.years');
		year.addEventListener('change', yearSelect);

		function yearSelect() {
			console.log(yearSelect.value);
		}

		new Chart(ctx, {
			type: 'line',
			data: {
				labels: weeks,
				datasets: [
					{
						label: 'Cocaine',
						data: keywords,
						parsing: {
							yAxisKey: 'cocaine'
						}
					},
					{
						label: 'GHB',
						data: keywords,
						parsing: {
							yAxisKey: 'ghb'
						}
					},
					{
						label: 'XTC',
						data: keywords,
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
	<select class="years">
		<option value="2022">2022</option>
		<option value="2021">2021</option>
		<option value="2020">2020</option>
		<option value="2019">2019</option>
	</select>
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
