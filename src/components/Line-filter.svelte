<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	/* Load weeks dataset for consistent x-axis */
	import { weeks } from '../data/weeks';

	/* Load events datafor consistent week tooltips */
	import { events } from '../data/events';

	/* Load datasets for cocaine per year */
	import { cocaineTweets } from '../data/years/cocaine_tweets';
	import { cocaineNews } from '../data/years/cocaine_news';
	import { cocaineTrends } from '../data/years/cocaine_trends';

	/* Load datasets for XTC per year */
	import { xtcTweets } from '../data/years/xtc_tweets';
	import { xtcNews } from '../data/years/xtc_news';
	import { xtcTrends } from '../data/years/xtc_trends';

	/* Load datasets for ghb per year */

	onMount(async () => {
		const ctx = document.getElementById('Line');

		/* Get value from Year input */
		const year = document.querySelector('.years');
		year.addEventListener('change', yearSelect);

		/* Get value from drug input */
		const drug = document.querySelector('.drugs');
		drug.addEventListener('change', drugSelect);

		let scoresTweets = [];
		let scoresNews = [];
		let scoresTrends = [];

		/* Initial score for the charts (default 2022)*/

		for (let item of cocaineTweets[2022]) {
			scoresTweets.push(item.score);
		}

		for (let item of cocaineNews[2022]) {
			scoresNews.push(item.score);
		}

		for (let item of cocaineTrends[2022]) {
			scoresTrends.push(item.score);
		}

		function drugSelect() {
			console.log(drug.value);

			if (drug.value === 'xtc') {
				for (let item of xtcTweets[year.value]) {
					scoresTweets.push(item.score);
				}

				for (let item of xtcNews[year.value]) {
					scoresNews.push(item.score);
				}

				for (let item of xtcTrends[year.value]) {
					scoresTrends.push(item.score);
				}
			} else if (drug.value === 'cocaine') {
				for (let item of cocaineTweets[year.value]) {
					scoresTweets.push(item.score);
				}

				for (let item of cocaineNews[year.value]) {
					scoresNews.push(item.score);
				}

				for (let item of cocaineTrends[year.value]) {
					scoresTrends.push(item.score);
				}
			}
			myChart.data.datasets[0].data = scoresTweets;
			myChart.data.datasets[1].data = scoresNews;
			myChart.data.datasets[2].data = scoresTrends;
			myChart.update();

			scoresTweets = [];
			scoresNews = [];
			scoresTrends = [];
		}

		function yearSelect() {
			drugSelect();
		}

		const myChart = new Chart(ctx, {
			type: 'line',
			data: {
				labels: weeks,
				datasets: [
					{
						label: 'Tweets',
						data: scoresTweets,
						parsing: {
							yAxisKey: 'score',
							xAxisKey: 'week'
						},
						backgroundColor: '#6cbcbd',
						borderColor: '#6cbcbd'
					},
					{
						label: 'News',
						data: scoresNews,
						parsing: {
							yAxisKey: 'score',
							xAxisKey: 'week'
						},
						backgroundColor: '#ed6d85',
						borderColor: '#ed6d85'
					},
					{
						label: 'Trends',
						data: scoresTrends,
						parsing: {
							yAxisKey: 'score',
							xAxisKey: 'week'
						}
					},
					{
						label: 'Events',
						data: events,
						type: 'bar',
						parsing: {
							yAxisKey: 'score'
						},
						backgroundColor: 'rgba(54, 162, 235, 0.2)'
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
	<h3>Interest over time per year for a specific drug</h3>
	<div>
		<select class="years">
			<option value="2022">2022</option>
			<option value="2021">2021</option>
		</select>
		<select class="drugs">
			<option value="cocaine">Cocaine</option>
			<option value="ghb">GHB</option>
			<option value="xtc">XTC</option>
		</select>
	</div>
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
