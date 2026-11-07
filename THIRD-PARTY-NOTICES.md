# Third-party notices

Undaergo bundles third-party software and derives map, place and routing data from third-party
datasets. Every notice and licence text ships **inside the installation**: the `licenses/` directory in
this repository is a mirror of the one the installer places beside the application, and the
application's `Settings` view opens it.

The enumerated list — every component, its copyright notice, its licence and the file carrying the
terms — is [licenses/NOTICE-bundle.txt](licenses/NOTICE-bundle.txt). Read that file first; it is the
authoritative record and it travels with the product.

## What the application itself carries

| Component | Version | Licence |
| --- | --- | --- |
| Electron, Node.js | 44.10.1 | MIT |
| Chromium (bundled with Electron) | 44.10.1 | BSD-3-Clause and others |
| React, React DOM | 19.3.0 | MIT |
| Zustand | 5.0.15 | MIT |
| TanStack Query | 5.102.8 | MIT |
| MapLibre GL JS | 6.9.0 | BSD-3-Clause |
| PMTiles | 4.5.0 | BSD-3-Clause |
| Lucide React | 1.46.0 | ISC |
| docx-templates | 4.15.0 | MIT |
| JSZip | 3.10.2 | MIT |
| sax | 1.3.0 | ISC |
| Valhalla routing engine | 3.9.0 | MIT |
| Valhalla's bundled libraries (27 DLLs) | with 3.9.0 | LGPL-2.1, MPL-2.0, Apache-2.0, MIT, BSD, ISC, zlib, IJG |
| Noto Sans Regular and Medium (map glyphs) | subset | SIL Open Font License 1.1 |

Electron's and Chromium's own notices are installed as `LICENSE.electron.txt` and
`LICENSES.chromium.html` in the application folder by Electron itself.

The map style follows the visual design of OpenFreeMap's Liberty style, itself derived from OSM Liberty
and OSM Bright — style code BSD-3-Clause, design CC BY 4.0 and CC BY 3.0. The style shipped here is a
port of that look onto the Protomaps schema, not a copy of the upstream style document.

## The data files

| File | Source | Licence |
| --- | --- | --- |
| `italy.pmtiles` | Protomaps build of OpenStreetMap, Italy, build 20260915 | ODbL 1.0 |
| `poi-overture.sqlite` | Overture Maps Foundation, places theme, release 2026-08-19.0 | CDLA-Permissive-2.0, with Apache-2.0 (Foursquare) and CC0-1.0 (AllThePlaces) contributions |
| `routing-italy-3.9.0.tar.gz` | Routing graph tiled by Valhalla from a Geofabrik OpenStreetMap extract of Italy | ODbL 1.0 |

Two OpenStreetMap-derived files are also compiled into the application itself, and are therefore
distributed with every instalment: `rail-overview.geo.json` (the railway network at low zoom) and
`admin-labels.geo.json` (region and province label points). `italy-outline.geo.json` (the national
outline used to clip the place data) derives from Overture Maps.

## The database the application builds

Importing the place file writes a database under the operator's own data directory. The importer also
adds the place, street and locality names it reads from the installed map, so that database is a
Derivative Database under the ODbL as well as a collection of Overture records. It is not distributed
by the application. An operator who passes it on or publishes it must comply with both licences,
including the ODbL share-alike obligation — see [licenses/NOTICE-places.txt](licenses/NOTICE-places.txt).

## If you pass a data file on

The ODbL requires that a recipient of an OpenStreetMap-derived database also receives the licence, and
Apache-2.0 requires its NOTICE to be retained. Pass on the file together with this directory:

- `licenses/LICENSE-ODbL-1.0.txt` for the map archive and the routing graph,
- `licenses/LICENSE-CDLA-Permissive-2.0.txt` and `licenses/LICENSE-Apache-2.0.txt` for the place data,
- `licenses/NOTICE-places.txt` and `licenses/NOTICE-routing.txt` for the attributions.

The "© OpenStreetMap contributors" credit drawn on the map must not be removed from a redistribution of
the map or routing data.

## Changes to this file

The register of components lives in [licenses/NOTICE-bundle.txt](licenses/NOTICE-bundle.txt) and is
updated there, in the same change that adds, removes or upgrades a bundled library. This file is
updated when a release changes a dataset's release identifier or licence.
