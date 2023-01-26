<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	import { ChoroplethChart } from 'chartjs-chart-geo';
	import { feature } from 'topojson-client';
	import { bind } from '../../src/nice-select2.js';

	/* Load datasets for events and drugs */
	import { cocaineAde } from '../data/map/ade_cocaine';
	import { ghbAde } from '../data/map/ade_ghb';
	import { xtcAde } from '../data/map/ade_xtc';

	import { cocaineCarnaval } from '../data/map/carnaval_cocaine';
	import { ghbCarnaval } from '../data/map/carnaval_ghb';
	import { xtcCarnaval } from '../data/map/carnaval_xtc';

	import { cocaineKingsday } from '../data/map/kingsday_cocaine';
	import { ghbKingsday } from '../data/map/kingsday_ghb';
	import { xtcKingsday } from '../data/map/kingsday_xtc';

	import { cocaineLowlands } from '../data/map/lowlands_cocaine';
	import { ghbLowlands } from '../data/map/lowlands_ghb';
	import { xtcLowlands } from '../data/map/lowlands_xtc';

	import { cocainePride } from '../data/map/pride_cocaine';
	import { ghbPride } from '../data/map/pride_ghb';
	import { xtcPride } from '../data/map/pride_xtc';

	// import { cocaineAde } from '../data/map/ade_cocaine';

	onMount(async () => {
		const ctx = document.getElementById('Map');

		bind(document.querySelector('.years'));
		bind(document.querySelector('.event'));
		bind(document.querySelector('.drug'));

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

				let data = cocaineKingsday[2022];

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
					} else if (event.value === 'ade') {
						if (drug.value === 'cocaine') {
							cocaineAde[year.value][0].feature = ni;
							cocaineAde[year.value][1].feature = nb;
							cocaineAde[year.value][2].feature = ut;
							cocaineAde[year.value][3].feature = zh;
							cocaineAde[year.value][4].feature = nh;
							cocaineAde[year.value][5].feature = sa;
							cocaineAde[year.value][6].feature = st;
							cocaineAde[year.value][7].feature = bo;
							cocaineAde[year.value][8].feature = dr;
							cocaineAde[year.value][9].feature = fr;
							cocaineAde[year.value][10].feature = ge;
							cocaineAde[year.value][11].feature = gr;
							cocaineAde[year.value][12].feature = li;
							cocaineAde[year.value][13].feature = ov;
							cocaineAde[year.value][14].feature = fl;
							cocaineAde[year.value][15].feature = ze;
							data = cocaineAde[year.value];
						} else if (drug.value === 'ghb') {
							ghbAde[year.value][0].feature = ni;
							ghbAde[year.value][1].feature = nb;
							ghbAde[year.value][2].feature = ut;
							ghbAde[year.value][3].feature = zh;
							ghbAde[year.value][4].feature = nh;
							ghbAde[year.value][5].feature = sa;
							ghbAde[year.value][6].feature = st;
							ghbAde[year.value][7].feature = bo;
							ghbAde[year.value][8].feature = dr;
							ghbAde[year.value][9].feature = fr;
							ghbAde[year.value][10].feature = ge;
							ghbAde[year.value][11].feature = gr;
							ghbAde[year.value][12].feature = li;
							ghbAde[year.value][13].feature = ov;
							ghbAde[year.value][14].feature = fl;
							ghbAde[year.value][15].feature = ze;
							data = ghbAde[year.value];
						} else {
							xtcAde[year.value][0].feature = ni;
							xtcAde[year.value][1].feature = nb;
							xtcAde[year.value][2].feature = ut;
							xtcAde[year.value][3].feature = zh;
							xtcAde[year.value][4].feature = nh;
							xtcAde[year.value][5].feature = sa;
							xtcAde[year.value][6].feature = st;
							xtcAde[year.value][7].feature = bo;
							xtcAde[year.value][8].feature = dr;
							xtcAde[year.value][9].feature = fr;
							xtcAde[year.value][10].feature = ge;
							xtcAde[year.value][11].feature = gr;
							xtcAde[year.value][12].feature = li;
							xtcAde[year.value][13].feature = ov;
							xtcAde[year.value][14].feature = fl;
							xtcAde[year.value][15].feature = ze;
							data = xtcAde[year.value];
						}
					} else if (event.value === 'carnaval') {
						if (drug.value === 'cocaine') {
							cocaineCarnaval[year.value][0].feature = ni;
							cocaineCarnaval[year.value][1].feature = nb;
							cocaineCarnaval[year.value][2].feature = ut;
							cocaineCarnaval[year.value][3].feature = zh;
							cocaineCarnaval[year.value][4].feature = nh;
							cocaineCarnaval[year.value][5].feature = sa;
							cocaineCarnaval[year.value][6].feature = st;
							cocaineCarnaval[year.value][7].feature = bo;
							cocaineCarnaval[year.value][8].feature = dr;
							cocaineCarnaval[year.value][9].feature = fr;
							cocaineCarnaval[year.value][10].feature = ge;
							cocaineCarnaval[year.value][11].feature = gr;
							cocaineCarnaval[year.value][12].feature = li;
							cocaineCarnaval[year.value][13].feature = ov;
							cocaineCarnaval[year.value][14].feature = fl;
							cocaineCarnaval[year.value][15].feature = ze;
							data = cocaineCarnaval[year.value];
						} else if (drug.value === 'ghb') {
							ghbCarnaval[year.value][0].feature = ni;
							ghbCarnaval[year.value][1].feature = nb;
							ghbCarnaval[year.value][2].feature = ut;
							ghbCarnaval[year.value][3].feature = zh;
							ghbCarnaval[year.value][4].feature = nh;
							ghbCarnaval[year.value][5].feature = sa;
							ghbCarnaval[year.value][6].feature = st;
							ghbCarnaval[year.value][7].feature = bo;
							ghbCarnaval[year.value][8].feature = dr;
							ghbCarnaval[year.value][9].feature = fr;
							ghbCarnaval[year.value][10].feature = ge;
							ghbCarnaval[year.value][11].feature = gr;
							ghbCarnaval[year.value][12].feature = li;
							ghbCarnaval[year.value][13].feature = ov;
							ghbCarnaval[year.value][14].feature = fl;
							ghbCarnaval[year.value][15].feature = ze;
							data = ghbCarnaval[year.value];
						} else {
							xtcCarnaval[year.value][0].feature = ni;
							xtcCarnaval[year.value][1].feature = nb;
							xtcCarnaval[year.value][2].feature = ut;
							xtcCarnaval[year.value][3].feature = zh;
							xtcCarnaval[year.value][4].feature = nh;
							xtcCarnaval[year.value][5].feature = sa;
							xtcCarnaval[year.value][6].feature = st;
							xtcCarnaval[year.value][7].feature = bo;
							xtcCarnaval[year.value][8].feature = dr;
							xtcCarnaval[year.value][9].feature = fr;
							xtcCarnaval[year.value][10].feature = ge;
							xtcCarnaval[year.value][11].feature = gr;
							xtcCarnaval[year.value][12].feature = li;
							xtcCarnaval[year.value][13].feature = ov;
							xtcCarnaval[year.value][14].feature = fl;
							xtcCarnaval[year.value][15].feature = ze;
							data = xtcCarnaval[year.value];
						}
					} else if (event.value === 'lowlands') {
						if (drug.value === 'cocaine') {
							cocaineLowlands[year.value][0].feature = ni;
							cocaineLowlands[year.value][1].feature = nb;
							cocaineLowlands[year.value][2].feature = ut;
							cocaineLowlands[year.value][3].feature = zh;
							cocaineLowlands[year.value][4].feature = nh;
							cocaineLowlands[year.value][5].feature = sa;
							cocaineLowlands[year.value][6].feature = st;
							cocaineLowlands[year.value][7].feature = bo;
							cocaineLowlands[year.value][8].feature = dr;
							cocaineLowlands[year.value][9].feature = fr;
							cocaineLowlands[year.value][10].feature = ge;
							cocaineLowlands[year.value][11].feature = gr;
							cocaineLowlands[year.value][12].feature = li;
							cocaineLowlands[year.value][13].feature = ov;
							cocaineLowlands[year.value][14].feature = fl;
							cocaineLowlands[year.value][15].feature = ze;
							data = cocaineLowlands[year.value];
						} else if (drug.value === 'ghb') {
							ghbLowlands[year.value][0].feature = ni;
							ghbLowlands[year.value][1].feature = nb;
							ghbLowlands[year.value][2].feature = ut;
							ghbLowlands[year.value][3].feature = zh;
							ghbLowlands[year.value][4].feature = nh;
							ghbLowlands[year.value][5].feature = sa;
							ghbLowlands[year.value][6].feature = st;
							ghbLowlands[year.value][7].feature = bo;
							ghbLowlands[year.value][8].feature = dr;
							ghbLowlands[year.value][9].feature = fr;
							ghbLowlands[year.value][10].feature = ge;
							ghbLowlands[year.value][11].feature = gr;
							ghbLowlands[year.value][12].feature = li;
							ghbLowlands[year.value][13].feature = ov;
							ghbLowlands[year.value][14].feature = fl;
							ghbLowlands[year.value][15].feature = ze;
							data = ghbLowlands[year.value];
						} else {
							xtcLowlands[year.value][0].feature = ni;
							xtcLowlands[year.value][1].feature = nb;
							xtcLowlands[year.value][2].feature = ut;
							xtcLowlands[year.value][3].feature = zh;
							xtcLowlands[year.value][4].feature = nh;
							xtcLowlands[year.value][5].feature = sa;
							xtcLowlands[year.value][6].feature = st;
							xtcLowlands[year.value][7].feature = bo;
							xtcLowlands[year.value][8].feature = dr;
							xtcLowlands[year.value][9].feature = fr;
							xtcLowlands[year.value][10].feature = ge;
							xtcLowlands[year.value][11].feature = gr;
							xtcLowlands[year.value][12].feature = li;
							xtcLowlands[year.value][13].feature = ov;
							xtcLowlands[year.value][14].feature = fl;
							xtcLowlands[year.value][15].feature = ze;
							data = xtcLowlands[year.value];
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

<section>
	<h1>Searches per region</h1>
	<p>Shows the Google Keywords searches per region (provinces) on a relative (0, 100) scale.</p>
	<ul class="filter">
		<select id="years" class="years">
			<option selected="selected" value="2022">2022</option>
			<option value="2021">2021</option>
			<option value="2020">2020</option>
			<option value="2019">2019</option>
			<option value="2018">2018</option>
		</select>
		<select class="event">
			<option selected="selected" value="kingsday">Kingsday</option>
			<option value="lowlands">Lowlands</option>
			<option value="carnaval">Carnaval</option>
			<option value="pride">Pride</option>
			<option value="ade">ADE</option>
		</select>
		<select class="drug">
			<option selected="selected" value="cocaine">Cocaine</option>
			<option value="ghb">GHB</option>
			<option value="xtc">XTC</option>
		</select>
	</ul>
</section>
<canvas id="Map" />

<style>
	canvas {
		transform: translateX(-30em) translateY(5em);
	}

	ul {
		position: absolute;
		display: flex;
	}

	select {
		display: none;
	}

	section {
		width: 25em;
		line-height: 1.6;
		z-index: 1;
	}

	.filter {
		padding: 0;
	}

	h1 {
		color: #5188cb;
	}
</style>
