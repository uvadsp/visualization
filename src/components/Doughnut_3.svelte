<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { xtcRelated } from '../data/related/xtc_related';

	onMount(async () => {
		let labelsxtc = [];
		let relatedxtc = [];

		console.log(xtcRelated);

		let year = 2020;

		for (let item of xtcRelated[year]) {
			labelsxtc.push(item.drug);
		}

		for (let item of xtcRelated[year]) {
			relatedxtc.push(item.score);
		}

		console.log(labelsxtc);
		console.log(relatedxtc);

		const ctx = document.getElementById('DoughnutThree');

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
				labels: labelsxtc,
				datasets: [
					{
						data: relatedxtc
					}
				]
			}
		});
	});
</script>

<article>
	<h3><strong>XTC</strong> also searched for:</h3>
	<div class="container">
		<canvas id="DoughnutThree" />
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
		grid-column: 5 / 7;
		grid-row: 5 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
