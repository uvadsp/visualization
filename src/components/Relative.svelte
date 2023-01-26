<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	/* Load weeks dataset for consistent x-axis */
	import { weeks } from '../data/weeks';

	/* Load datasets for cocaine per year */
	import { cocaineRelative } from '../data/relative/cocaine_relative';
	import { ghbRelative } from '../data/relative/ghb_relative';
	import { xtcRelative } from '../data/relative/xtc_relative';

	onMount(async () => {
		const ctx = document.getElementById('relative');

		const year = document.querySelector('.years');
		year.addEventListener('change', covidSelect);

		/* Get value from drug input */
		const drug = document.querySelector('.drugs');
		drug.addEventListener('change', covidSelect);

		let scoresTrends = [];

		for (let item of cocaineRelative[year.value]) {
			scoresTrends.push(item.score);
		}

		function covidSelect() {
			const currentYear = document.querySelector('.currentYear');
			currentYear.textContent = `current: ${year.value}`;

			const currentDrug = document.querySelector('.currentDrug');
			currentDrug.textContent = `current: ${drug.value}`;

			if (drug.value === 'xtc') {
				for (let item of xtcRelative[year.value]) {
					scoresTrends.push(item.score);
				}
			} else if (drug.value === 'cocaine') {
				for (let item of cocaineRelative[year.value]) {
					scoresTrends.push(item.score);
				}
			} else {
				for (let item of ghbRelative[year.value]) {
					scoresTrends.push(item.score);
				}
			}
			myChart.data.datasets[0].data = scoresTrends;
			myChart.update();

			scoresTrends = [];
		}

		const myChart = new Chart(ctx, {
			type: 'line',
			data: {
				labels: weeks,
				datasets: [
					{
						label: 'Trends',
						data: scoresTrends,
						parsing: {
							yAxisKey: 'score',
							xAxisKey: 'week'
						},
						backgroundColor: '#e2ba56',
						borderColor: '#e2ba56'
					}
				]
			},
			options: {
				responsive: true,
				maintainAspectRatio: false,
				scales: {
					y: {
						suggestedMax: 100
					}
				}
			},
			parsing: {
				xAxisKey: 'weeks'
			}
		});
	});
</script>

<article>
	<h3>
		Relative over all years (<span class="currentYear">year: 2022</span>
		<span class="currentDrug">drug: cocaine</span>)
	</h3>
	<div class="container">
		<canvas id="relative" />
	</div>
</article>

<style>
	h3 {
		font-weight: 500;
		color: #5188cb;
	}

	div {
		display: flex;
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
		grid-column: 4 / 7;
		grid-row: 6 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
