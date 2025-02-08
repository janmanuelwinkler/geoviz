
# GeoViz Tutorials
This repository is a collection of tutorials that should help you rendering maps on the Web. The main objective of these tutorials is to illustrate how to add layers of data to base maps, leveraging different protocols for different mapping needs. For this, we will be using the amazing [maplibre-gl-js](https://github.com/maplibre/maplibre-gl-js) library. Most of the tutorials will have code examples in two different flavour: plain HTML, as well as [Vue 3](https://vuejs.org) components.

## Tutorial outline
This repo provides a practical, hands-on approach to display maps on the Web. We will cover all the steps involved in displaying data localized on maps, in an incremental fashion. 

| Module | Description | Status |
|--------|-------------|--------|
| [Getting Started](./0_getting-started) | Set up your dev environment for the main tutorials | ✅ | 
| [Display a Base Map](./1_simple-map) | Learn how to use [maplibre-gl-js](https://github.com/maplibre/maplibre-gl-js) to display a base map| ✅ |
| [Working with PMTiles files](./2_PMTiles-map) | Learn how to access `PMTiles` files using the `pmtiles` protocol and display tiled data on a base map | ✅ |
| [Working with Cloud Optimized GEOTiff files](./3_Cloud-Optimized-GeoTIFF) | Learn how to access `COG` files to display data on a base map | 🚧 WIP |
| [Dynamically Load Layers](./4_layer-list) | Create a list of available layers and dynamically toggle them on a base map | 🚧 WIP | 

## Prerequisites
Before starting, ensure you have the following:
- Basic understanding of maps and HTML/Web development.
- Familiarity with Python, HTML/Vue and the [GeoPandas](https://geopandas.org/en/stable/) library.
- Access to a AWS S3 bucket for some of the tutorials (more info in the [Getting Started](./0_getting-started) tutorial).

## Tech stack

The tutorials in this repository leverage the following tech stack

- Python3 and shell scripts for [data processing](./dataprocessing).
-  [Vue 3](https://vuejs.org), TypeScript, [Vuetify](https://vuetifyjs.com/en/) and [Vite](https://vitejs.dev) to build the tutorials [website](./site).

### Recommended Setup

- [VS Code](https://code.visualstudio.com/) + [Vue - Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (previously Volar) and disable Vetur.

## License
Licensed under the [MIT license](LICENSE).
