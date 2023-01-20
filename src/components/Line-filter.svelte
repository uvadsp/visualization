<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { weeks } from '../data/weeks';
	import { tweets } from '../data/years/cocaine_tweets';
	import { news } from '../data/years/cocaine_news';
	import { events } from '../data/events';

	console.log(tweets);

	onMount(async () => {
		const ctx = document.getElementById('Line');

		/* Get value from Year input */
		const year = document.querySelector('.years');
		year.addEventListener('change', yearSelect);

		let scoresTweets = [];
		let scoresNews = [];

		for (let item of tweets[2022]) {
			scoresTweets.push(item.score); // Will display contents of the object inside the array
		}

		for (let item of news[2022]) {
			scoresNews.push(item.score); // Will display contents of the object inside the array
		}

		function yearSelect() {
			for (let item of tweets[year.value]) {
				scoresTweets.push(item.score); // Will display contents of the object inside the array
			}

			for (let item of news[year.value]) {
				scoresNews.push(item.score); // Will display contents of the object inside the array
			}

			myChart.data.datasets[0].data = scoresTweets;
			myChart.data.datasets[1].data = scoresNews;
			myChart.update();
			scoresTweets = [];
			scoresNews = [];
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
		<select class="drug">
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
