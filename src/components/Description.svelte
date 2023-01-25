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

		const kingsdayEvent = document.querySelector('.kingsdayEvent');
		const lowlandsEvent = document.querySelector('.lowlandsEvent');
		const crossEvent = document.querySelector('.crossEvent');
		const prideEvent = document.querySelector('.prideEvent');
		const adeEvent = document.querySelector('.adeEvent');
		const christmasEvent = document.querySelector('.christmasEvent');
		const eveEvent = document.querySelector('.eveEvent');

		kingsday.addEventListener('click', function () {
			kingsdayEvent.classList.add('show');
			lowlandsEvent.classList.replace('show', 'hidden');
			crossEvent.classList.replace('show', 'hidden');
			prideEvent.classList.replace('show', 'hidden');
			christmasEvent.classList.replace('show', 'hidden');
			eveEvent.classList.replace('show', 'hidden');
			adeEvent.classList.replace('show', 'hidden');
		});

		lowlands.addEventListener('click', function () {
			kingsdayEvent.classList.replace('show', 'hidden');
			lowlandsEvent.classList.add('show');
			crossEvent.classList.replace('show', 'hidden');
			prideEvent.classList.replace('show', 'hidden');
			christmasEvent.classList.replace('show', 'hidden');
			eveEvent.classList.replace('show', 'hidden');
			adeEvent.classList.replace('show', 'hidden');
		});

		cross.addEventListener('click', function () {
			kingsdayEvent.classList.replace('show', 'hidden');
			lowlandsEvent.classList.replace('show', 'hidden');
			crossEvent.classList.add('show');
			prideEvent.classList.replace('show', 'hidden');
			christmasEvent.classList.replace('show', 'hidden');
			eveEvent.classList.replace('show', 'hidden');
			adeEvent.classList.replace('show', 'hidden');
		});

		pride.addEventListener('click', function () {
			kingsdayEvent.classList.replace('show', 'hidden');
			lowlandsEvent.classList.replace('show', 'hidden');
			crossEvent.classList.replace('show', 'hidden');
			prideEvent.classList.add('show');
			christmasEvent.classList.replace('show', 'hidden');
			eveEvent.classList.replace('show', 'hidden');
			adeEvent.classList.replace('show', 'hidden');
		});

		christmas.addEventListener('click', function () {
			kingsdayEvent.classList.replace('show', 'hidden');
			lowlandsEvent.classList.replace('show', 'hidden');
			crossEvent.classList.replace('show', 'hidden');
			prideEvent.classList.replace('show', 'hidden');
			christmasEvent.classList.add('show');
			eveEvent.classList.replace('show', 'hidden');
			adeEvent.classList.replace('show', 'hidden');
		});

		eve.addEventListener('click', function () {
			kingsdayEvent.classList.replace('show', 'hidden');
			lowlandsEvent.classList.replace('show', 'hidden');
			crossEvent.classList.replace('show', 'hidden');
			prideEvent.classList.replace('show', 'hidden');
			christmasEvent.classList.replace('show', 'hidden');
			eveEvent.classList.add('show');
			adeEvent.classList.replace('show', 'hidden');
		});

		ade.addEventListener('click', function () {
			kingsdayEvent.classList.replace('show', 'hidden');
			lowlandsEvent.classList.replace('show', 'hidden');
			crossEvent.classList.replace('show', 'hidden');
			prideEvent.classList.replace('show', 'hidden');
			christmasEvent.classList.replace('show', 'hidden');
			eveEvent.classList.replace('show', 'hidden');
			adeEvent.classList.add('show');
		});
	});
</script>

<article>
	<div class="container show kingsdayEvent">
		<h3>Event description: Kingsday</h3>
		<p>
			Koningsdag or King's Day is a national holiday in the Kingdom of the Netherlands. Celebrated
			on 27 April, the date marks the birth of King Willem-Alexander. Koningsdag is known for its
			nationwide vrijmarkt ("free market"), at which the Dutch sell their used items.
		</p>
		<h4>Date(s): 27 April (26 April if 27 April is a Sunday)</h4>
		<h4>Drug popularity:</h4>
		<ul>
			<li>
				<span>GHB:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
			<li>
				<span>XTC:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
		</ul>
	</div>
	<div />

	<div class="container hidden prideEvent">
		<h3>Event description: Pride</h3>
		<p>
			Koningsdag or King's Day is a national holiday in the Kingdom of the Netherlands. Celebrated
			on 27 April, the date marks the birth of King Willem-Alexander. Koningsdag is known for its
			nationwide vrijmarkt ("free market"), at which the Dutch sell their used items.
		</p>
		<h4>Date(s): 27 April (26 April if 27 April is a Sunday)</h4>
		<h4>Drug popularity:</h4>
		<ul>
			<li>
				<span>GHB:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
			<li>
				<span>XTC:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
		</ul>
	</div>
	<div />

	<div class="container hidden crossEvent">
		<h3>Event description: De Zwarte Cross</h3>
		<p>
			Koningsdag or King's Day is a national holiday in the Kingdom of the Netherlands. Celebrated
			on 27 April, the date marks the birth of King Willem-Alexander. Koningsdag is known for its
			nationwide vrijmarkt ("free market"), at which the Dutch sell their used items.
		</p>
		<h4>Date(s): 27 April (26 April if 27 April is a Sunday)</h4>
		<h4>Drug popularity:</h4>
		<ul>
			<li>
				<span>GHB:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
			<li>
				<span>XTC:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
		</ul>
	</div>
	<div />

	<div class="container hidden lowlandsEvent">
		<h3>Event description: Lowlands</h3>
		<p>
			Koningsdag or King's Day is a national holiday in the Kingdom of the Netherlands. Celebrated
			on 27 April, the date marks the birth of King Willem-Alexander. Koningsdag is known for its
			nationwide vrijmarkt ("free market"), at which the Dutch sell their used items.
		</p>
		<h4>Date(s): 27 April (26 April if 27 April is a Sunday)</h4>
		<h4>Drug popularity:</h4>
		<ul>
			<li>
				<span>GHB:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
			<li>
				<span>XTC:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
		</ul>
	</div>
	<div />

	<div class="container hidden christmasEvent">
		<h3>Event description: Christmas</h3>
		<p>
			Koningsdag or King's Day is a national holiday in the Kingdom of the Netherlands. Celebrated
			on 27 April, the date marks the birth of King Willem-Alexander. Koningsdag is known for its
			nationwide vrijmarkt ("free market"), at which the Dutch sell their used items.
		</p>
		<h4>Date(s): 27 April (26 April if 27 April is a Sunday)</h4>
		<h4>Drug popularity:</h4>
		<ul>
			<li>
				<span>GHB:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
			<li>
				<span>XTC:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
		</ul>
	</div>
	<div />

	<div class="container hidden eveEvent">
		<h3>Event description: New Years Eve</h3>
		<p>
			Koningsdag or King's Day is a national holiday in the Kingdom of the Netherlands. Celebrated
			on 27 April, the date marks the birth of King Willem-Alexander. Koningsdag is known for its
			nationwide vrijmarkt ("free market"), at which the Dutch sell their used items.
		</p>
		<h4>Date(s): 27 April (26 April if 27 April is a Sunday)</h4>
		<h4>Drug popularity:</h4>
		<ul>
			<li>
				<span>GHB:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
			<li>
				<span>XTC:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
		</ul>
	</div>
	<div />

	<div class="container hidden adeEvent">
		<h3>Event description: ADE</h3>
		<p>
			Koningsdag or King's Day is a national holiday in the Kingdom of the Netherlands. Celebrated
			on 27 April, the date marks the birth of King Willem-Alexander. Koningsdag is known for its
			nationwide vrijmarkt ("free market"), at which the Dutch sell their used items.
		</p>
		<h4>Date(s): 27 April (26 April if 27 April is a Sunday)</h4>
		<h4>Drug popularity:</h4>
		<ul>
			<li>
				<span>GHB:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
			<li>
				<span>XTC:</span>
				<div class="border">
					<div class="fill" />
				</div>
			</li>
		</ul>
	</div>
	<div />
	<img src="/images/kingsday.jpg" />
</article>

<style>
	img {
		max-width: 100%;
		width: 13em;
		object-fit: cover;
		height: 19.1em;
	}
	h3 {
		color: #5188cb;
		font-weight: 500;
	}

	.container {
		display: flex;
		flex-direction: column;
		width: 100%;
		height: 100%;
	}

	.container p {
		width: 30em;
		margin-right: 6em;
		font-size: 0.8em;
	}

	.container ul {
		font-size: 0.8em;
	}

	.border {
		border: 1px solid black;
		border-radius: 0.2em;
		height: 0.5em;
		width: 20em;
	}

	h4 {
		padding: 0;
		margin-top: 0;
		margin-bottom: 0.5em;
		font-size: 0.9em;
	}

	ul li {
		display: flex;
		align-items: center;
	}

	ul {
		padding: 0;
		margin: 0;
		list-style-type: none;
	}

	ul span {
		margin-right: 0.5em;
	}

	.fill {
		width: 80%;
		height: 0.5em;
		background: orange;
	}
	article {
		display: flex;
		padding: 0em 2em 2em 2em;
		border-radius: 0.2em;
		background: white;
		grid-column: 2 / 6;
		grid-row: 6 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}

	.hidden {
		display: none;
	}

	.show {
		display: block;
	}
</style>
