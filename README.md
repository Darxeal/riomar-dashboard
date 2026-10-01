# Fair2Adapt App

<!-- QUALITY_BADGE_START -->
[![Software quality](https://img.shields.io/badge/FAIRness-80%25-green "score: 80% | passed: 33 | failed: 8 | errors: 0")](RSFC_REPORT.md)
<!-- QUALITY_BADGE_END -->
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19163889.svg)](https://doi.org/10.5281/zenodo.19163889)
[![Project Status: Active](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)

WebGL-based interactive globe viewer for FAIR Digital Objects, built on [GridLook](https://github.com/observingClouds/gridlook). Part of the [FAIR2Adapt](https://fair2adapt-eosc.eu) project.

Supports HEALPix DGGS (including multiscale pyramids), curvilinear, regular, triangular, Gaussian reduced, and irregular grids from cloud-hosted Zarr datasets.

![](docs/assets/showcase.webp)

## Features

- **Multiple grid types**: HEALPix, curvilinear, regular, triangular, Gaussian reduced, irregular
- **Token authentication**: access private datasets via `::token=` URL parameter
- **RO-Crate resolution**: paste an RO-Crate PID to auto-discover and load the dataset
- **Interactive controls**: colormaps, bounds, projections, time/dimension slicing
- **MapLibre basemaps**: OSM, EMODNET bathymetry, satellite
- **Interactive charts**: pick a location, bounding box or polygon; plot over time (or other dimension, e.g. depth)

## Try It Live

**Dashboard**:
- https://f2a.plan4all.eu/ (Plan4all)
- https://fair2adapt.github.io/riomar-dashboard/ (GitHub Pages)

**With FDO2map**: https://fair2adapt.github.io/FDO2map/ — paste an RO-Crate PID to resolve and visualize

### Example datasets

```
# RiOMAR ocean model (HEALPix)
https://f2a.plan4all.eu/#https://pangeo-eosc-minioapi.vm.fedcloud.eu/afouilloux-riomar/small_hp_pyramid.zarr

# RiOMAR ocean model 2 (HEALPix)
https://f2a.plan4all.eu/#https://pangeo-eosc-minioapi.vm.fedcloud.eu/afouilloux-riomar/small_test1_hp_fixed.zarr

# Private dataset with API key
https://f2a.plan4all.eu/#https://fair2adapt.duckdns.org/bucket/dataset.zarr::token=YOUR_API_KEY
```

The same URLs work with `https://fair2adapt.github.io/riomar-dashboard/` as the base.

## URL format

```
https://f2a.plan4all.eu/#<ZARR_URL>::param1=value1::param2=value2
```

| Parameter | Description |
|-----------|-------------|
| `token` | API key for authenticated proxy |
| `varname` | Variable to display |
| `colormap` | Colormap name |
| `boundlow` / `boundhigh` | Color scale bounds |

## Installation

Requires [Node.js](https://nodejs.org/) (v18+) and [npm](https://www.npmjs.com/).

```bash
git clone https://github.com/FAIR2Adapt/riomar-dashboard.git
cd riomar-dashboard
npm install
```

## Development

```bash
npm run dev        # Dev server on localhost:5173
npm run build      # Production build
npm run typecheck  # Type checking
npm run lint       # Linting
```

## Deployment

The dashboard is deployed as a static site to two places:

- **GitHub Pages** (https://fair2adapt.github.io/riomar-dashboard/) via the `deploy.yml` workflow, which runs only in `FAIR2Adapt/riomar-dashboard`.
- **Plan4all** (https://f2a.plan4all.eu/) via the `deploy-lesprojekt.yml` workflow, which runs only in `LESPROJEKT/fair2adapt-app` (self-hosted runner).

To deploy elsewhere, run `npm run build` and serve the `dist/` directory.

## Acknowledgements

Based on [GridLook](https://github.com/observingClouds/gridlook) by Tobias Kölling and contributors. Extended with RO-Crate resolution, token authentication, and MapLibre basemaps for the FAIR2Adapt project.

## License

[MIT](LICENSE)