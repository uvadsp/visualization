<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { ChoroplethChart } from 'chartjs-chart-geo';
	import { feature } from 'topojson-client';

	onMount(async () => {
		const ctx = document.getElementById('Map');

		fetch('https://cdn.jsdelivr.net/npm/us-atlas/states-10m.json')
			.then((r) => r.json())
			.then((us) => {
				console.log(us);
				const nation = feature(us, us.objects.nation).features;
				const states = feature(us, us.objects.states).features;

				new ChoroplethChart(ctx, {
					type: 'choropleth',
					data: {
						labels: states.map((d) => d.properties.name),
						datasets: [
							{
								label: 'States',
								outline: nation,
								data: states.map((d) => ({ feature: d, value: Math.random() * 50 }))
							}
						]
					},
					options: {
						plugins: {
							legend: {
								display: false
							}
						},
						scales: {
							projection: {
								axis: 'x',
								projection: 'albersUsa'
							},
							color: {
								axis: 'x',
								quantize: 5,
								legend: {
									position: 'bottom-right',
									align: 'bottom'
								}
							}
						}
					}
				});
			});
	});
</script>

<canvas id="Map" />
