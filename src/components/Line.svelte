<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { trends } from '../data/popularity/cocaine_trends';
	import { news } from '../data/popularity/cocaine_news';
	import { tweets } from '../data/popularity/cocaine_tweets';
	import { events } from '../data/events';

	const labels = [];
	const cleaning = trends.forEach((x, i) => labels.push(x.week));
	console.log(labels);

	console.log(trends);

	console.log(events);

	onMount(async () => {
		const ctx = document.getElementById('Line');

		new Chart(ctx, {
			type: 'line',
			data: {
				labels: labels,
				datasets: [
					{
						label: 'Google Trends',
						data: trends,
						parsing: {
							yAxisKey: 'score',
							xAxisKey: 'week'
						},
						backgroundColor: '#FFB1C1',
						borderColor: '#FFB1C1'
					},
					{
						label: 'News Articles',
						data: news,
						parsing: {
							yAxisKey: 'score',
							xAxisKey: 'week'
						},
						backgroundColor: '#57a0e5',
						borderColor: '#57a0e5'
					},
					{
						label: 'Tweets',
						data: tweets,
						parsing: {
							yAxisKey: 'score',
							xAxisKey: 'week'
						},
						backgroundColor: '#6cbcbd',
						borderColor: '#6cbcbd'
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
	<h3>Interest over time 2022</h3>
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
