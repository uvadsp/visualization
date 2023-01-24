<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { ChoroplethChart } from 'chartjs-chart-geo';
	import { feature } from 'topojson-client';

	/* Load datasets for events and drugs */
	import { cocaineKingsday } from '../data/map/kingsday_cocaine';

	onMount(async () => {
		const ctx = document.getElementById('Map');

		async function load(url) {
			const res = await fetch(
				'https://raw.githubusercontent.com/deldersveld/topojson/master/continents/europe.json'
			);
			const item = await res.json();
			return item;
		}

		/* ✨ Prettiest code you will ever see. Be prepared 🙈 But yea it has works */

		const countries = await load();

		const country = feature(countries, countries.objects.continent_Europe_subunits).features;

		const Netherlands = country.find((d) => d.properties.geounit === 'Netherlands');

		fetch('https://raw.githubusercontent.com/markmarkoh/datamaps/master/src/js/data/nld.topo.json')
			.then((r) => r.json())
			.then((us) => {
				const states = feature(us, us.objects.nld).features;

				/* Buiten nederland */
				const ni = states.find((d) => d.properties.name === null);
				const sa = states.find((d) => d.properties.name === 'Saba');
				const st = states.find((d) => d.properties.name === 'St. Eustatius');
				const bo = states.find((d) => d.properties.name === 'Bonaire');

				/* Binnen nederland */
				const gr = states.find((d) => d.properties.name === 'Groningen');
				const fr = states.find((d) => d.properties.name === 'Friesland');
				const dr = states.find((d) => d.properties.name === 'Drenthe');
				const fl = states.find((d) => d.properties.name === 'Flevoland');
				const ov = states.find((d) => d.properties.name === 'Overijssel');
				const ut = states.find((d) => d.properties.name === 'Utrecht');
				const ge = states.find((d) => d.properties.name === 'Gelderland');
				const zh = states.find((d) => d.properties.name === 'Zuid-Holland');
				const ze = states.find((d) => d.properties.name === 'Zeeland');
				const nh = states.find((d) => d.properties.name === 'Noord-Holland');
				const nb = states.find((d) => d.properties.name === 'Noord-Brabant');
				const li = states.find((d) => d.properties.name === 'Limburg');

				/* Get value from Year input */
				const year = document.querySelector('.years');
				year.addEventListener('change', filterYear);

				let data = cocaineKingsday[2019];

				/* Default year features */
				/* Buiten nederland */
				cocaineKingsday[2019][0].feature = ni;
				cocaineKingsday[2019][1].feature = nb;
				cocaineKingsday[2019][2].feature = ut;
				cocaineKingsday[2019][3].feature = zh;

				/* Binnen nederland */
				cocaineKingsday[2019][4].feature = nh;
				cocaineKingsday[2019][5].feature = sa;
				cocaineKingsday[2019][6].feature = st;
				cocaineKingsday[2019][7].feature = bo;
				cocaineKingsday[2019][8].feature = dr;
				cocaineKingsday[2019][9].feature = fr;
				cocaineKingsday[2019][10].feature = ge;
				cocaineKingsday[2019][11].feature = gr;
				cocaineKingsday[2019][12].feature = li;
				cocaineKingsday[2019][13].feature = ov;
				cocaineKingsday[2019][14].feature = fl;
				cocaineKingsday[2019][15].feature = ze;

				function filterYear() {
					data = cocaineKingsday[year.value];
					console.log(year.value);
					console.log(data);

					/* Buiten nederland */
					cocaineKingsday[year.value][0].feature = ni;
					cocaineKingsday[year.value][1].feature = nb;
					cocaineKingsday[year.value][2].feature = ut;
					cocaineKingsday[year.value][3].feature = zh;

					/* Binnen nederland */
					cocaineKingsday[year.value][4].feature = nh;
					cocaineKingsday[year.value][5].feature = sa;
					cocaineKingsday[year.value][6].feature = st;
					cocaineKingsday[year.value][7].feature = bo;
					cocaineKingsday[year.value][8].feature = dr;
					cocaineKingsday[year.value][9].feature = fr;
					cocaineKingsday[year.value][10].feature = ge;
					cocaineKingsday[year.value][11].feature = gr;
					cocaineKingsday[year.value][12].feature = li;
					cocaineKingsday[year.value][13].feature = ov;
					cocaineKingsday[year.value][14].feature = fl;
					cocaineKingsday[year.value][15].feature = ze;

					myChart.data.datasets[0].data = data;
					myChart.update();
					data = [];
				}

				const myChart = new ChoroplethChart(ctx, {
					type: 'choropleth',
					data: {
						labels: states.map((d) => d.properties.name),
						datasets: [
							{
								label: 'States',
								outline: Netherlands,
								data: data
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

<ul>
	<select class="years">
		<option value="2018">2018</option>
		<option value="2019">2019</option>
	</select>
	<select class="event">
		<option value="king">Kingsday</option>
		<option value="pride">Pride</option>
		<option value="lowlands">Lowlands</option>
		<option value="cross">Zwarte Cross</option>
		<option value="christmas">Christmas</option>
		<option value="new">New Year's Eve</option>
	</select>
	<select class="drug">
		<option value="cocaine">cocaine</option>
		<option value="ghb">ghb</option>
		<option value="ghb">xtc</option>
	</select>
</ul>
<canvas id="Map" />

<style>
	canvas {
		transform: translateY(5em);
	}

	ul {
		position: absolute;
	}
</style>
