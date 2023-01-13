<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {
		const ctx = document.getElementById('Line');

		new Chart(ctx, {
			type: 'line',
			data: {
				datasets: [
					{
						label: 'Google Trends',
						data: [
							{
								date: '2018-01-28',
								cocaine: 45
							},
							{
								date: '2018-02-11',
								cocaine: 48
							},
							{
								date: '2018-02-25',
								cocaine: 42
							},
							{
								date: '2018-03-11',
								cocaine: 45
							},
							{
								date: '2018-04-01',
								cocaine: 50
							},
							{
								date: '2018-04-15',
								cocaine: 38
							},
							{
								date: '2018-05-06',
								cocaine: 43
							},
							{
								date: '2018-06-03',
								cocaine: 38
							},
							{
								date: '2018-06-24',
								cocaine: 54
							},
							{
								date: '2018-07-22',
								cocaine: 51
							},
							{
								date: '2018-08-12',
								cocaine: 51
							},
							{
								date: '2018-09-02',
								cocaine: 52
							},
							{
								date: '2018-09-16',
								cocaine: 49
							},
							{
								date: '2018-10-14',
								cocaine: 51
							},
							{
								date: '2018-11-04',
								cocaine: 52
							},
							{
								date: '2018-11-25',
								cocaine: 46
							},
							{
								date: '2018-12-09',
								cocaine: 50
							},
							{
								date: '2018-12-23',
								cocaine: 52
							},
							{
								date: '2019-01-20',
								cocaine: 42
							},
							{
								date: '2019-02-10',
								cocaine: 59
							},
							{
								date: '2019-03-03',
								cocaine: 39
							},
							{
								date: '2019-03-31',
								cocaine: 55
							},
							{
								date: '2019-04-28',
								cocaine: 41
							},
							{
								date: '2019-05-12',
								cocaine: 44
							},
							{
								date: '2019-06-09',
								cocaine: 48
							},
							{
								date: '2019-07-14',
								cocaine: 67
							},
							{
								date: '2019-07-28',
								cocaine: 42
							},
							{
								date: '2019-08-11',
								cocaine: 41
							},
							{
								date: '2019-09-01',
								cocaine: 40
							},
							{
								date: '2019-09-15',
								cocaine: 50
							},
							{
								date: '2019-10-13',
								cocaine: 53
							},
							{
								date: '2019-11-10',
								cocaine: 55
							},
							{
								date: '2019-12-08',
								cocaine: 51
							},
							{
								date: '2019-12-22',
								cocaine: 43
							},
							{
								date: '2020-01-12',
								cocaine: 49
							},
							{
								date: '2020-01-26',
								cocaine: 48
							},
							{
								date: '2020-02-16',
								cocaine: 49
							},
							{
								date: '2020-03-08',
								cocaine: 55
							},
							{
								date: '2020-03-22',
								cocaine: 38
							},
							{
								date: '2020-04-12',
								cocaine: 49
							},
							{
								date: '2020-05-03',
								cocaine: 61
							},
							{
								date: '2020-05-17',
								cocaine: 41
							},
							{
								date: '2020-05-31',
								cocaine: 43
							},
							{
								date: '2020-06-28',
								cocaine: 46
							},
							{
								date: '2020-07-12',
								cocaine: 44
							},
							{
								date: '2020-08-09',
								cocaine: 65
							},
							{
								date: '2020-08-23',
								cocaine: 42
							},
							{
								date: '2020-10-04',
								cocaine: 46
							},
							{
								date: '2020-10-18',
								cocaine: 45
							},
							{
								date: '2020-11-08',
								cocaine: 47
							},
							{
								date: '2020-11-22',
								cocaine: 59
							},
							{
								date: '2020-12-27',
								cocaine: 57
							},
							{
								date: '2021-01-17',
								cocaine: 44
							},
							{
								date: '2021-02-07',
								cocaine: 40
							},
							{
								date: '2021-02-21',
								cocaine: 46
							},
							{
								date: '2021-03-14',
								cocaine: 43
							},
							{
								date: '2021-04-04',
								cocaine: 51
							},
							{
								date: '2021-05-09',
								cocaine: 44
							},
							{
								date: '2021-05-23',
								cocaine: 100
							},
							{
								date: '2021-06-06',
								cocaine: 44
							},
							{
								date: '2021-06-27',
								cocaine: 59
							},
							{
								date: '2021-07-18',
								cocaine: 51
							},
							{
								date: '2021-08-15',
								cocaine: 49
							},
							{
								date: '2021-09-12',
								cocaine: 52
							},
							{
								date: '2021-10-17',
								cocaine: 43
							},
							{
								date: '2021-12-12',
								cocaine: 41
							},
							{
								date: '2021-12-26',
								cocaine: 60
							},
							{
								date: '2022-01-23',
								cocaine: 48
							},
							{
								date: '2022-02-06',
								cocaine: 41
							},
							{
								date: '2022-03-06',
								cocaine: 45
							},
							{
								date: '2022-04-03',
								cocaine: 46
							},
							{
								date: '2022-04-24',
								cocaine: 52
							},
							{
								date: '2022-05-08',
								cocaine: 47
							},
							{
								date: '2022-05-22',
								cocaine: 40
							},
							{
								date: '2022-06-12',
								cocaine: 41
							},
							{
								date: '2022-07-10',
								cocaine: 43
							},
							{
								date: '2022-07-31',
								cocaine: 42
							},
							{
								date: '2022-08-14',
								cocaine: 39
							},
							{
								date: '2022-08-28',
								cocaine: 41
							},
							{
								date: '2022-09-18',
								cocaine: 56
							},
							{
								date: '2022-10-02',
								cocaine: 45
							},
							{
								date: '2022-10-23',
								cocaine: 44
							},
							{
								date: '2022-12-04',
								cocaine: 57
							},
							{
								date: '2022-12-18',
								cocaine: 56
							}
						]
					}
				]
			},
			options: {
				responsive: true,
				maintainAspectRatio: false,
				scales: {
					type: 'category',
					y: {
						beginAtZero: true
					}
				},
				parsing: {
					xAxisKey: 'date',
					yAxisKey: 'cocaine'
				}
			}
		});
	});
</script>

<article>
	<h3>Interest over time</h3>
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
