<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { ghbRelated } from '../data/related/ghb_related';

	onMount(async () => {
		let labelsghb = [];
		let relatedghb = [];

		for (let item of ghbRelated[2022]) {
			labelsghb.push(item.drug);
		}

		for (let item of ghbRelated[2022]) {
			relatedghb.push(item.score);
		}

		const year = document.querySelector('.years');
		/* Get value from Year input */
		year.addEventListener('change', yearSelect);

		function yearSelect() {
			for (let item of ghbRelated[year.value]) {
				labelsghb.push(item.drug);
			}

			for (let item of ghbRelated[year.value]) {
				relatedghb.push(item.score);
			}

			myChart.data.labels = labelsghb;
			myChart.data.datasets[0].data = relatedghb;
			myChart.update();

			labelsghb = [];
			relatedghb = [];
		}

		const ctx = document.getElementById('DoughnutTwo');

		const myChart = new Chart(ctx, {
			type: 'polarArea',
			options: {
				responsive: true,
				maintainAspectRatio: false,
				plugins: {
					legend: {
						display: true,
						position: 'bottom'
					}
				},
				scales: {
					r: {
						pointLabels: {
							display: true,
							centerPointLabels: true,
							font: {
								size: 12
							}
						}
					}
				}
			},
			data: {
				labels: labelsghb,
				datasets: [
					{
						data: relatedghb
					}
				]
			}
		});
	});
</script>

<article>
	<h3><strong>GHB</strong> also searched for:</h3>
	<div class="container">
		<canvas id="DoughnutTwo" />
	</div>
</article>

<style>
	h3 {
		font-weight: 500;
		color: #1433dd;
		margin-left: 2em;
	}

	.container {
		width: 100%;
		height: 100%;
	}

	article {
		padding-bottom: 4em;
		display: flex;
		justify-content: flex-start;
		flex-direction: column;
		align-items: flex-start;
		border-radius: 0.2em;
		background: white;
		grid-column: 3 / 5;
		grid-row: 5 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
