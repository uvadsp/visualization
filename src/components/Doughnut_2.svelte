<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { ghbRelated } from '../data/related/ghb_related';

	onMount(async () => {
		let labelsghb = [];
		let relatedghb = [];

		console.log(ghbRelated);

		let year = 2020;

		for (let item of ghbRelated[year]) {
			labelsghb.push(item.drug);
		}

		for (let item of ghbRelated[year]) {
			relatedghb.push(item.score);
		}

		console.log(labelsghb);
		console.log(relatedghb);

		const ctx = document.getElementById('DoughnutTwo');

		new Chart(ctx, {
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
