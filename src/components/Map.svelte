<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { ChoroplethChart } from 'chartjs-chart-geo';
	import { feature } from 'topojson-client';

	/* Load datasets for events and drugs */
	import { cocaineKingsday } from '../data/map/kingsday_cocaine';
	import { ghbKingsday } from '../data/map/kingsday_ghb';
	import { xtcKingsday } from '../data/map/kingsday_xtc';

	import { cocainePride } from '../data/map/pride_cocaine';
	import { ghbPride } from '../data/map/pride_ghb';
	import { xtcPride } from '../data/map/pride_xtc';

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

				const drug = document.querySelector('.drug');
				drug.addEventListener('change', filterYear);

				const event = document.querySelector('.event');
				event.addEventListener('change', filterYear);

				console.log(`Initial drug: ${drug.value}`);
				console.log(`Initial year: ${year.value}`);
				console.log(`Initial event: ${event.value}`);

				/* Initial filter value */

				let data = cocaineKingsday[2019];

				cocaineKingsday[year.value][0].feature = ni;
				cocaineKingsday[year.value][1].feature = nb;
				cocaineKingsday[year.value][2].feature = ut;
				cocaineKingsday[year.value][3].feature = zh;
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

				function filterYear() {
					if (event.value === 'kingsday') {
						if (drug.value === 'cocaine') {
							cocaineKingsday[year.value][0].feature = ni;
							cocaineKingsday[year.value][1].feature = nb;
							cocaineKingsday[year.value][2].feature = ut;
							cocaineKingsday[year.value][3].feature = zh;
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
							data = cocaineKingsday[year.value];
						} else if (drug.value === 'ghb') {
							ghbKingsday[year.value][0].feature = ni;
							ghbKingsday[year.value][1].feature = nb;
							ghbKingsday[year.value][2].feature = ut;
							ghbKingsday[year.value][3].feature = zh;
							ghbKingsday[year.value][4].feature = nh;
							ghbKingsday[year.value][5].feature = sa;
							ghbKingsday[year.value][6].feature = st;
							ghbKingsday[year.value][7].feature = bo;
							ghbKingsday[year.value][8].feature = dr;
							ghbKingsday[year.value][9].feature = fr;
							ghbKingsday[year.value][10].feature = ge;
							ghbKingsday[year.value][11].feature = gr;
							ghbKingsday[year.value][12].feature = li;
							ghbKingsday[year.value][13].feature = ov;
							ghbKingsday[year.value][14].feature = fl;
							ghbKingsday[year.value][15].feature = ze;
							data = ghbKingsday[year.value];
						} else {
							xtcKingsday[year.value][0].feature = ni;
							xtcKingsday[year.value][1].feature = nb;
							xtcKingsday[year.value][2].feature = ut;
							xtcKingsday[year.value][3].feature = zh;
							xtcKingsday[year.value][4].feature = nh;
							xtcKingsday[year.value][5].feature = sa;
							xtcKingsday[year.value][6].feature = st;
							xtcKingsday[year.value][7].feature = bo;
							xtcKingsday[year.value][8].feature = dr;
							xtcKingsday[year.value][9].feature = fr;
							xtcKingsday[year.value][10].feature = ge;
							xtcKingsday[year.value][11].feature = gr;
							xtcKingsday[year.value][12].feature = li;
							xtcKingsday[year.value][13].feature = ov;
							xtcKingsday[year.value][14].feature = fl;
							xtcKingsday[year.value][15].feature = ze;
							data = xtcKingsday[year.value];
						}
					} else if (event.value === 'pride') {
						if (drug.value === 'cocaine') {
							cocainePride[year.value][0].feature = ni;
							cocainePride[year.value][1].feature = nb;
							cocainePride[year.value][2].feature = ut;
							cocainePride[year.value][3].feature = zh;
							cocainePride[year.value][4].feature = nh;
							cocainePride[year.value][5].feature = sa;
							cocainePride[year.value][6].feature = st;
							cocainePride[year.value][7].feature = bo;
							cocainePride[year.value][8].feature = dr;
							cocainePride[year.value][9].feature = fr;
							cocainePride[year.value][10].feature = ge;
							cocainePride[year.value][11].feature = gr;
							cocainePride[year.value][12].feature = li;
							cocainePride[year.value][13].feature = ov;
							cocainePride[year.value][14].feature = fl;
							cocainePride[year.value][15].feature = ze;
							data = cocainePride[year.value];
						} else if (drug.value === 'ghb') {
							ghbPride[year.value][0].feature = ni;
							ghbPride[year.value][1].feature = nb;
							ghbPride[year.value][2].feature = ut;
							ghbPride[year.value][3].feature = zh;
							ghbPride[year.value][4].feature = nh;
							ghbPride[year.value][5].feature = sa;
							ghbPride[year.value][6].feature = st;
							ghbPride[year.value][7].feature = bo;
							ghbPride[year.value][8].feature = dr;
							ghbPride[year.value][9].feature = fr;
							ghbPride[year.value][10].feature = ge;
							ghbPride[year.value][11].feature = gr;
							ghbPride[year.value][12].feature = li;
							ghbPride[year.value][13].feature = ov;
							ghbPride[year.value][14].feature = fl;
							ghbPride[year.value][15].feature = ze;
							data = ghbPride[year.value];
						} else {
							xtcPride[year.value][0].feature = ni;
							xtcPride[year.value][1].feature = nb;
							xtcPride[year.value][2].feature = ut;
							xtcPride[year.value][3].feature = zh;
							xtcPride[year.value][4].feature = nh;
							xtcPride[year.value][5].feature = sa;
							xtcPride[year.value][6].feature = st;
							xtcPride[year.value][7].feature = bo;
							xtcPride[year.value][8].feature = dr;
							xtcPride[year.value][9].feature = fr;
							xtcPride[year.value][10].feature = ge;
							xtcPride[year.value][11].feature = gr;
							xtcPride[year.value][12].feature = li;
							xtcPride[year.value][13].feature = ov;
							xtcPride[year.value][14].feature = fl;
							xtcPride[year.value][15].feature = ze;
							data = xtcPride[year.value];
						}
					}

					console.log(`Updated drug: ${drug.value}`);
					console.log(`Updated year: ${year.value}`);
					console.log(`Updated event: ${event.value}`);
					console.log(data);

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
		<option selected="selected" value="2019">2019</option>
	</select>
	<select class="event">
		<option selected="selected" value="kingsday">Kingsday</option>
		<option value="pride">Pride</option>
	</select>
	<select class="drug">
		<option selected="selected" value="cocaine">cocaine</option>
		<option value="ghb">ghb</option>
		<option value="xtc">xtc</option>
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
