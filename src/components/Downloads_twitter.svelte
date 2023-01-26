<article>
	<h3>
		<svg xmlns="http://www.w3.org/2000/svg" xml:space="preserve" viewBox="0 0 248 204">
			<path
				fill="#a6aab1"
				d="M221.95 51.29c.15 2.17.15 4.34.15 6.53 0 66.73-50.8 143.69-143.69 143.69v-.04c-27.44.04-54.31-7.82-77.41-22.64 3.99.48 8 .72 12.02.73 22.74.02 44.83-7.61 62.72-21.66-21.61-.41-40.56-14.5-47.18-35.07 7.57 1.46 15.37 1.16 22.8-.87-23.56-4.76-40.51-25.46-40.51-49.5v-.64c7.02 3.91 14.88 6.08 22.92 6.32C11.58 63.31 4.74 33.79 18.14 10.71c25.64 31.55 63.47 50.73 104.08 52.76-4.07-17.54 1.49-35.92 14.61-48.25 20.34-19.12 52.33-18.14 71.45 2.19 11.31-2.23 22.15-6.38 32.07-12.26-3.77 11.69-11.66 21.62-22.2 27.93 10.01-1.18 19.79-3.86 29-7.95-6.78 10.16-15.32 19.01-25.2 26.16z"
			/>
		</svg>
		Tweets Datasets
	</h3>
	<ul>
		<li>
			<p>Name</p>
			<p>Timescale</p>
			<p>File</p>
		</li>
		<li>
			<p>Relative values for Cocaine</p>
			<p class="years">years</p>
			<a href="/downloads/relative_tweet_values_cocaine.csv" download class="downloads">Download</a>
		</li>
		<li>
			<p>Relative values for GHB</p>
			<p class="years">years</p>
			<p class="downloads">Download</p>
		</li>
		<li>
			<p>Relative values for XTC</p>
			<p class="years">years</p>
			<p class="downloads">Download</p>
		</li>
	</ul>
</article>

<style>
	h3 {
		color: #5188cb;
		font-weight: 500;
		padding: 1em 1.6em;
		margin: 0;
		display: flex;
		align-items: center;
	}

	h3 svg {
		margin-right: 1em;
		width: 1em;
	}

	ul li:first-of-type {
		display: flex;
		align-items: center;
		justify-content: space-between;
		background: rgb(240, 246, 254);
		padding: 0.6em 2em;
		font-weight: 500;
	}

	ul li p {
		margin: 0;
	}

	ul li {
		padding: 1em;
		display: flex;
		align-items: center;
	}

	ul li:not(:first-child) p:nth-child(1) {
		margin-right: 2em;
		width: 20em;
	}

	ul li:not(:first-child) p:nth-child(2) {
		margin-right: 9em;
	}

	ul li:not(:last-of-type) {
		border-bottom: 1px solid rgb(213, 219, 226);
	}

	.container {
		width: 100%;
		height: 80%;
	}

	ul {
		margin: 0;
		padding: 0;
		list-style-type: none;
	}

	article {
		display: flex;
		padding: 0em;
		flex-direction: column;
		border-radius: 0.2em;
		color: rgb(73, 85, 103);
		background: white;
		grid-column: 4 / 8;
		grid-row: 3 / 9;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}

	.years {
		background: rgb(243, 245, 247);
		border-radius: 12px;
		padding: 0.2em 1em;
		color: #3d8ad0;
	}

	.downloads {
		background: #3d8ad0;
		border-radius: 3px;
		padding: 0.5em 1em;
		color: white;
		cursor: pointer;
		transition: 250ms ease;
	}

	.downloads:hover {
		background: #1e5b94;
	}

	a {
		text-decoration: none;
	}
</style>
