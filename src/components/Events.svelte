<script>
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';

	onMount(async () => {
		/* I know that there are data attributes and loops 🙃 */
		const kingsday = document.querySelector('.kingsday');
		const lowlands = document.querySelector('.lowlands');
		const cross = document.querySelector('.cross');
		const pride = document.querySelector('.pride');
		const ade = document.querySelector('.ade');
		const christmas = document.querySelector('.christmas');
		const eve = document.querySelector('.eve');

		kingsday.addEventListener('click', function () {
			kingsday.classList.add('active');
			lowlands.classList.remove('active');
			cross.classList.remove('active');
			pride.classList.remove('active');
			christmas.classList.remove('active');
			eve.classList.remove('active');
			ade.classList.remove('active');
		});

		lowlands.addEventListener('click', function () {
			kingsday.classList.remove('active');
			lowlands.classList.add('active');
			cross.classList.remove('active');
			pride.classList.remove('active');
			christmas.classList.remove('active');
			eve.classList.remove('active');
			ade.classList.remove('active');
		});

		cross.addEventListener('click', function () {
			kingsday.classList.remove('active');
			lowlands.classList.remove('active');
			cross.classList.add('active');
			pride.classList.remove('active');
			christmas.classList.remove('active');
			eve.classList.remove('active');
			ade.classList.remove('active');
		});

		ade.addEventListener('click', function () {
			kingsday.classList.remove('active');
			lowlands.classList.remove('active');
			cross.classList.remove('active');
			pride.classList.remove('active');
			christmas.classList.remove('active');
			eve.classList.remove('active');
			ade.classList.add('active');
		});

		pride.addEventListener('click', function () {
			kingsday.classList.remove('active');
			lowlands.classList.remove('active');
			cross.classList.remove('active');
			pride.classList.add('active');
			christmas.classList.remove('active');
			eve.classList.remove('active');
			ade.classList.remove('active');
		});

		christmas.addEventListener('click', function () {
			kingsday.classList.remove('active');
			lowlands.classList.remove('active');
			cross.classList.remove('active');
			pride.classList.remove('active');
			christmas.classList.add('active');
			eve.classList.remove('active');
			ade.classList.remove('active');
		});

		eve.addEventListener('click', function () {
			kingsday.classList.remove('active');
			lowlands.classList.remove('active');
			cross.classList.remove('active');
			pride.classList.remove('active');
			christmas.classList.remove('active');
			eve.classList.add('active');
			ade.classList.remove('active');
		});
	});
</script>

<article>
	<h3>Select event  </h3>
	<ul class="eventsList">
		<li class="kingsday">
			<span />Kings Day
		</li>
		<li class="lowlands"><span />Lowlands</li>
		<li class="cross"><span />Zwarte Cross</li>
		<li class="pride"><span />Pride Adam</li>
		<li class="ade">
			<span />ADE
		</li>
		<li class="christmas"><span />Christmas</li>
		<li class="eve"><span />New Year's Eve</li>
	</ul>
</article>

<style>
	h3 {
		color: #5188cb;
		font-weight: 500;
		margin-top: 0;
		margin-bottom: 1em;
	}
	ul li span {
		width: 0.5em;
		height: 0.5em;
		border-radius: 100%;
		display: inline-block;
		margin-right: 1em;
	}

	ul {
		list-style-type: none;
		margin: 0;
		padding: 0;
	}

	ul li {
		font-size: 0.8em;
	}

	li {
		opacity: 0.5;
		transition: all 250ms ease;
	}

	li:hover {
		opacity: 1;
		cursor: pointer;
	}

	li.active {
		opacity: 1;
	}

	.eventsList li:nth-child(1) span {
		border: 1px solid rgba(253, 186, 116, 1);
	}

	.eventsList .active:nth-child(1) span {
		background-color: rgba(253, 186, 116, 1);
	}

	.eventsList li:nth-child(2) span {
		border: 1px solid rgba(126, 212, 171, 1);
	}

	.eventsList .active:nth-child(2) span {
		background-color: rgba(126, 212, 171, 1);
	}

	.eventsList li:nth-child(3) span {
		border: 1px solid rgba(120, 111, 167, 1);
	}

	.eventsList .active:nth-child(3) span {
		background-color: rgba(120, 111, 167, 1);
	}

	.eventsList li:nth-child(4) span {
		border: 1px solid rgba(116, 62, 228, 1);
	}

	.eventsList .active:nth-child(4) span {
		background-color: rgba(116, 62, 228, 1);
	}

	.eventsList li:nth-child(5) span {
		border: 1px solid rgba(254, 250, 83, 1);
	}

	.eventsList .active:nth-child(5) span {
		background-color: rgba(254, 250, 83, 1);
	}

	.eventsList li:nth-child(6) span {
		border: 1px solid rgba(221, 82, 76, 1);
	}

	.eventsList .active:nth-child(6) span {
		background-color: rgba(221, 82, 76, 1);
	}

	.eventsList li:nth-child(7) span {
		border: 1px solid rgba(233, 162, 59, 1);
	}

	.eventsList .active:nth-child(7) span {
		background-color: rgba(233, 162, 59, 1);
	}

	article {
		padding: 1.2em;
		border-radius: 0.2em;
		background: white;
		grid-column: 1 / 2;
		grid-row: 6 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}
</style>
