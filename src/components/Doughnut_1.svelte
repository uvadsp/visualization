<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { cocaineRelated } from '../data/related/cocaine_related';

	onMount(async () => {
		let labelscocaine = [];
		let relatedcocaine = [];

		console.log(cocaineRelated);

		let year = 2022;

		for (let item of cocaineRelated[year]) {
			labelscocaine.push(item.drug);
		}

		for (let item of cocaineRelated[year]) {
			relatedcocaine.push(item.score);
		}

		console.log(labelscocaine);
		console.log(relatedcocaine);

		const ctx = document.getElementById('DoughnutOne');

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
				labels: labelscocaine,
				datasets: [
					{
						data: relatedcocaine
					}
				]
			}
		});
	});
</script>

<article>
	<h3><strong>Cocaine</strong> also searched for:</h3>
	<div class="container">
		<canvas id="DoughnutOne" />
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
		grid-column: 1 / 3;
		grid-row: 5 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
