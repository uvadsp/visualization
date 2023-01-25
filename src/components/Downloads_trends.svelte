<article>
	<h3>
		<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"
			><path
				d="M6 12C6 15.3137 8.68629 18 12 18C14.6124 18 16.8349 16.3304 17.6586 14H12V10H21.8047V14H21.8C20.8734 18.5645 16.8379 22 12 22C6.47715 22 2 17.5228 2 12C2 6.47715 6.47715 2 12 2C15.445 2 18.4831 3.742 20.2815 6.39318L17.0039 8.68815C15.9296 7.06812 14.0895 6 12 6C8.68629 6 6 8.68629 6 12Z"
				fill="rgba(75, 85, 101, 0.5)"
			/></svg
		>Google Trends Datasets
	</h3>
	<ul>
		<li>
			<p>Name</p>
			<p>Timescale</p>
			<p>Download</p>
		</li>
		<li>
			<p>Relative values for Cocaine</p>
			<p class="years">Years</p>
			<p class="downloads">Download</p>
		</li>
		<li>
			<p>Relative values for GHB</p>
			<p class="years">Years</p>
			<p class="downloads">Download</p>
		</li>
		<li>
			<p>Relative values for XTC</p>
			<p class="years">Years</p>
			<p class="downloads">Download</p>
		</li>
	</ul>
</article>

<style>
	h3 {
		color: blue;
		font-weight: 500;
		padding: 1em 1.6em;
		margin: 0;
		display: flex;
		align-items: center;
	}

	h3 svg {
		margin-right: 1em;
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
		margin-right: 12em;
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
		grid-column: 1 / 4;
		grid-row: 2 / 5;
		box-shadow: 0px 10px 15px -3px #d3d0e5;
	}

	.years {
		background: rgb(243, 245, 247);
		border-radius: 12px;
		padding: 0.2em 1em;
		color: blue;
	}

	.downloads {
		background: blue;
		border-radius: 3px;
		padding: 0.5em 1em;
		color: white;
	}
</style>
