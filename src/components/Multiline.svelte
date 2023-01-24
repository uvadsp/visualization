<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	import { weeks } from '../data/weeks';

	/* Load datasets for reach drug */
	import { xtcTrends } from '../data/trends/xtc_trends';
	import { ghbTrends } from '../data/trends/ghb_trends';
	import { cocaineTrends } from '../data/trends/cocaine_trends';

	onMount(async () => {
		const ctx = document.getElementById('multiline');
		const year = document.querySelector('.years');
		/* Get value from Year input */
		year.addEventListener('change', yearSelect);

		let scoresxtc = [];
		let scoresghb = [];
		let scorescocaine = [];

		for (let item of xtcTrends[2022]) {
			scoresxtc.push(item.score);
		}

		for (let item of ghbTrends[2022]) {
			scoresghb.push(item.score);
		}

		for (let item of cocaineTrends[2022]) {
			scorescocaine.push(item.score);
		}

		function yearSelect() {
			for (let item of xtcTrends[year.value]) {
				scoresxtc.push(item.score);
			}

			for (let item of ghbTrends[year.value]) {
				scoresghb.push(item.score);
			}

			for (let item of cocaineTrends[year.value]) {
				scorescocaine.push(item.score);
			}

			myChart.data.datasets[0].data = scorescocaine;
			myChart.data.datasets[1].data = scoresghb;
			myChart.data.datasets[2].data = scoresxtc;
			myChart.update();

			scorescocaine = [];
			scoresghb = [];
			scoresxtc = [];
		}

		const myChart = new Chart(ctx, {
			type: 'line',
			data: {
				labels: weeks,
				datasets: [
					{
						label: 'Cocaine',
						data: scorescocaine,
						parsing: {
							yAxisKey: 'cocaine'
						}
					},
					{
						label: 'GHB',
						data: scoresghb,
						parsing: {
							yAxisKey: 'ghb'
						}
					},
					{
						label: 'XTC',
						data: scoresxtc,
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
		<option selected="selected" value="2022">2022</option>
		<option value="2021">2021</option>
		<option value="2020">2020</option>
		<option value="2019">2019</option>
		<option value="2018">2018</option>
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
