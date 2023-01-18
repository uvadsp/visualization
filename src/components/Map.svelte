<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { ChoroplethChart } from 'chartjs-chart-geo';
	import { feature } from 'topojson-client';

	onMount(async () => {
		const ctx = document.getElementById('Map');

		async function load(url) {
			const res = await fetch(
				'https://raw.githubusercontent.com/deldersveld/topojson/master/continents/europe.json'
			);
			const item = await res.json();
			return item;
		}

		const countries = await load();
		console.log(countries);

		const country = feature(countries, countries.objects.continent_Europe_subunits).features;
		console.log(country);

		const Netherlands = country.find((d) => d.properties.geounit === 'Netherlands');
		console.log(Netherlands);

		fetch('https://raw.githubusercontent.com/markmarkoh/datamaps/master/src/js/data/nld.topo.json')
			.then((r) => r.json())
			.then((us) => {
				console.log(us);
				const states = feature(us, us.objects.nld).features;

				new ChoroplethChart(ctx, {
					type: 'choropleth',
					data: {
						labels: states.map((d) => d.properties.name),
						datasets: [
							{
								label: 'States',
								outline: Netherlands,
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
								projection: 'transverseMercator'
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

<style>
	canvas {
		transform: translateY(5em);
	}
</style>
