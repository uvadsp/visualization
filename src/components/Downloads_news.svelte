<article>
	<h3>
		<svg
			width="424"
			height="143"
			viewBox="0 0 405 143"
			fill="none"
			xmlns="http://www.w3.org/2000/svg"
		>
			<path
				d="M119.434 139.629V3.465H83.25V40.621C83.25 51.707 83.449 69.801 84.422 75.828C81.5 70.183 69.442 52.098 63.219 43.734L33.266 3.465H0V139.629H36.184V98.004C36.184 86.914 35.989 68.824 35.016 62.793C38.516 68.824 50.184 86.332 56.215 94.699L88.699 139.629H119.434Z"
				fill="#A6AAB1"
			/>
			<path
				d="M404.891 97.809C404.891 72.329 389.719 61.825 355.485 53.653C337.977 49.567 333.126 47.235 333.126 42.173C333.126 37.31 335.845 33.81 347.126 33.81C360.931 33.81 372.985 38.482 385.056 46.65L403.345 17.084C388.938 6.965 372.211 1.328 349.07 1.328C316.187 1.328 295.379 18.64 295.379 44.312C295.379 71.546 311.141 80.496 344.008 88.078C362.289 92.363 367.156 95.473 367.156 100.527C367.156 106.949 362.875 109.285 349.453 109.285C336.812 109.285 319.5 102.473 309.578 95.676L291.297 125.231C305.496 134.567 326.703 141.77 348.672 141.77C381.359 141.77 404.891 128.926 404.891 97.809Z"
				fill="#A6AAB1"
			/>
			<path
				fill-rule="evenodd"
				clip-rule="evenodd"
				d="M174.758 71.258C174.758 51.953 190.406 36.301 209.711 36.301C229.02 36.301 244.672 51.953 244.672 71.258C244.672 90.567 229.02 106.215 209.711 106.215C190.406 106.215 174.758 90.566 174.758 71.258ZM138.453 71.258C138.453 31.902 170.355 0 209.711 0C249.067 0 280.973 31.902 280.973 71.258C280.973 110.614 249.067 142.52 209.711 142.52C170.355 142.52 138.453 110.613 138.453 71.258Z"
				fill="#A6AAB1"
			/>
		</svg>
		News Datasets
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
			<p class="downloads">Download</p>
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
		width: 2em;
		height: 1em;
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
		grid-column: 1 / 4;
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
