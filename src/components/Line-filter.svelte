<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { bind } from '../../src/nice-select2.js';

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

		bind(document.querySelector('.years'));
		bind(document.querySelector('.drugs'));

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

		const kingsday = document.querySelector('.kingsday');
		const lowlands = document.querySelector('.lowlands');
		const cross = document.querySelector('.cross');
		const pride = document.querySelector('.pride');
		const ade = document.querySelector('.ade');
		const christmas = document.querySelector('.christmas');
		const eve = document.querySelector('.eve');

		function highlight(
			number,
			color,
			number1,
			number2,
			number3,
			number4,
			number5,
			number6,
			color1
		) {
			myChart.data.datasets[3].backgroundColor[number] = color;
			myChart.data.datasets[3].backgroundColor[number1] = color1;
			myChart.data.datasets[3].backgroundColor[number2] = color1;
			myChart.data.datasets[3].backgroundColor[number3] = color1;
			myChart.data.datasets[3].backgroundColor[number4] = color1;
			myChart.data.datasets[3].backgroundColor[number5] = color1;
			myChart.data.datasets[3].backgroundColor[number6] = color1;
			myChart.update();
		}

		kingsday.addEventListener('click', function () {
			console.log('kingsday');
			highlight(
				'16',
				'rgb(243, 188, 127)',
				'27',
				'29',
				'32',
				'41',
				'50',
				'51',
				'rgba(112, 172, 230, 0.4)'
			);
		});

		lowlands.addEventListener('click', function () {
			console.log('lowlands');
			highlight('27', 'rgba(126, 212, 171, 1)');
		});

		cross.addEventListener('click', function () {
			console.log('cross');
			highlight('29', 'rgba(120, 111, 167, 1)');
		});

		pride.addEventListener('click', function () {
			console.log('pride');
			highlight('32', 'rgba(116, 62, 228, 1)');
		});

		ade.addEventListener('click', function () {
			console.log('ade');
			highlight('41', 'rgba(254, 250, 83, 1)');
		});

		christmas.addEventListener('click', function () {
			console.log('christmas');
			highlight('50', 'rgba(221, 82, 76, 1)');
		});

		eve.addEventListener('click', function () {
			console.log('eve');
			highlight('51', 'rgba(233, 162, 59, 1)');
		});

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
						backgroundColor: '#5baeec',
						borderColor: '#5baeec'
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
						},
						backgroundColor: '#eab83f',
						borderColor: '#eab83f'
					},
					{
						label: 'Events',
						data: events,
						backgroundColor: [
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgba(112, 172, 230, 0.4)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgba(112, 172, 230, 0.4)',
							'rgb(243, 188, 127, 1)',
							'rgba(112, 172, 230, 0.4)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgba(112, 172, 230, 0.4)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgba(112, 172, 230, 0.4)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgb(243, 188, 127, 1)',
							'rgba(112, 172, 230, 0.4)',
							'rgba(112, 172, 230, 0.4)'
						],
						type: 'bar',
						parsing: {
							yAxisKey: 'score'
						}
					}
				]
			},
			options: {
				responsive: true,
				maintainAspectRatio: false,
				plugins: {
					legend: {
						labels: {
							filter: (item) => {
								return item.text != 'Events';
							},
							usePointStyle: true,
							pointStyle: 'rectRot'
						}
					}
				},
				scales: {
					x: {
						title: {
							display: true,
							text: 'Weeknumbers'
						},
						ticks: {
							color: (c) => {
								if (c['tick']['value'] === 16) return 'rgb(243, 188, 127)';
								if (c['tick']['value'] === 27) return 'rgb(146, 210, 174)';
								if (c['tick']['value'] === 29) return 'rgb(250, 237, 108)';
								if (c['tick']['value'] === 32) return 'rgb(109, 64, 220)';
								if (c['tick']['value'] === 50) return 'rgb(205, 91, 82)';
								if (c['tick']['value'] === 51) return 'rgb(223, 165, 80)';
							}
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

		console.log(myChart);
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
		grid-column: 1 / 7;
		grid-row: 1 / 6;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
