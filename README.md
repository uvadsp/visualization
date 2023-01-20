# UVA Data Systems Project

> Web-based visualization for the Data Systems Project @uva for the Police Academy 

![GitHub banner](/docs/banner.jpg)

## Description

Digital dashboard for analysts at the Police Academy to allow to filter and explore the datasets. Project structure built with [SvelteKit](https://kit.svelte.dev) and charts created with [Chart.js](https://www.chartjs.org).

## Install

### Prerequisites

Make sure you have node and npm installed on your machine.

### Running

```
# start a development server with hmr
npm run dev

# build a statis version of the site
npm run build
```

Live version of the application is hosted on Netlify which uses the auto adapter for deployment.

## Project Structure

```
├── src                   # Svelte root folder
│   ├── components        # Svelte components
│   ├── datasets          # Raw .json files for data
│   └── routes            # Dashboard pages
├── static                # Fonts, images etc.
└── README.md

```

## License

Unless stated otherwise, code is [MIT][mit] © [Danny de Vries](https://github.com/dandevri) & docs and images are [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/).
