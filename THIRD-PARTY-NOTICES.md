# Third-party notices

This file records the third-party components included in the Undaergo application and the sources,
licences and modifications of the data files distributed with it. The application itself is
proprietary; see `LICENSE`. The data files are not part of the application and are not covered by its
licence.

When a data file is passed on to another person, this file and the `licenses/` directory must travel
with it. That is how the ODbL attribution and share-alike terms and the Apache-2.0 NOTICE reach the
recipient.

## Application components

| Component | Version | Licence | Copyright / source |
| --- | --- | --- | --- |
| Electron | 44.10.1 | MIT | Electron contributors; GitHub Inc. |
| Chromium | bundled with Electron 44.10.1 | BSD-3-Clause and other open-source licences | The Chromium Project and contributors |
| Node.js | bundled with Electron | MIT | Node.js contributors |
| React, React DOM | 19.3.0 | MIT | Meta Platforms, Inc. and affiliates |
| Zustand | 5.0.15 | MIT | Paul Henschel |
| TanStack Query | 5.102.8 | MIT | Tanner Linsley |
| MapLibre GL JS | 6.9.0 | BSD-3-Clause | MapLibre contributors |
| PMTiles | 4.5.0 | BSD-3-Clause | Protomaps LLC |
| Lucide React | 1.46.0 | ISC | Lucide Icons and contributors |
| Valhalla routing engine | 3.9.0 | MIT | Valhalla contributors; Mapillary AB, Mapzen |
| SQLite | bundled with Node.js | Public domain | D. Richard Hipp and contributors |
| Noto Sans Regular and Medium | glyph set built from the fonts | SIL Open Font License 1.1 | The Noto Project Authors |

The installed application carries Electron's own `LICENSE` and `LICENSES.chromium.html`, which contains
the complete set of Chromium third-party notices. Electron's licence is at
<https://github.com/electron/electron/blob/main/LICENSE>; Chromium's is at
<https://chromium.googlesource.com/chromium/src/+/main/LICENSE>.

The application's logo and interface are original works of the copyright holder and form part of the
Application. The map sprite sheet is generated from Lucide icons (ISC). The map glyphs are derived
from Noto Sans under the SIL Open Font License 1.1.

### Map style

The map style is written for this application against the Protomaps schema, but it follows the visual
design of **OpenFreeMap's Liberty style**, itself derived from OSM Liberty and OSM Bright. The upstream
style code is BSD-3-Clause and its design is CC BY 4.0; OSM Bright's design is CC BY 3.0 and
OpenMapTiles' design is CC BY 4.0. Copyright © Zsolt Ero, Mapbox, OpenMapTiles and the respective
contributors. The style here is a port of that look, not a copy of the upstream style document.

- OpenFreeMap: <https://github.com/hyperknot/openfreemap-styles> (MIT for the repository; Liberty's
  design and code as stated above).
- OSM Liberty: <https://github.com/maputnik/osm-liberty>.
- Creative Commons Attribution 4.0: <https://creativecommons.org/licenses/by/4.0/>.
- Creative Commons Attribution 3.0: <https://creativecommons.org/licenses/by/3.0/>.

Full licence texts are in the `licenses/` directory:

| Licence | File |
| --- | --- |
| ODbL 1.0 | `licenses/LICENSE-ODbL-1.0.txt` |
| CDLA-Permissive-2.0 | `licenses/LICENSE-CDLA-Permissive-2.0.txt` |
| Apache 2.0 | `licenses/LICENSE-Apache-2.0.txt` |
| MIT — Electron | `licenses/LICENSE-Electron-MIT.txt` |
| MIT — React | `licenses/LICENSE-React-MIT.txt` |
| MIT — Zustand | `licenses/LICENSE-Zustand-MIT.txt` |
| MIT — TanStack Query | `licenses/LICENSE-TanStack-Query-MIT.txt` |
| MIT — Valhalla | `licenses/LICENSE-Valhalla-MIT.txt` |
| BSD-3-Clause — MapLibre | `licenses/LICENSE-MapLibre-BSD-3-Clause.txt` |
| BSD-3-Clause — PMTiles | `licenses/LICENSE-PMTiles-BSD-3-Clause.txt` |
| ISC — Lucide | `licenses/LICENSE-Lucide-ISC.txt` |
| OFL 1.1 — Noto Sans | `licenses/LICENSE-OFL-1.1-Noto-Sans.txt` |

CC0 1.0 applies to the AllThePlaces contributions to the place data and requires no notice:
<https://creativecommons.org/publicdomain/zero/1.0/>. SQLite's public-domain dedication is at
<https://www.sqlite.org/copyright.html>.

## Map data — `italy.pmtiles`

- **Source:** OpenStreetMap, through a Protomaps build of Italy (build `20260915`), restricted to the
  bounding box `6.6,35.4,18.6,47.1`.
- **Publisher:** OpenStreetMap contributors.
- **Licence:** Open Database License, version 1.0 (ODbL 1.0).
- **Copyright:** © OpenStreetMap contributors,
  <https://www.openstreetmap.org/copyright>.
- **Modifications:** the archive is a regional extract of the Protomaps build. Undaergo draws it as
  supplied; it does not alter its features or names.

The map displays the credit "© OpenStreetMap contributors". A redistribution of this file must keep
that attribution and comply with the ODbL, including its share-alike obligation for a Derivative
Database.

## Place data — `poi-overture.sqlite`

- **Source:** Overture Maps Foundation, theme `places`, type `place`, release `2026-08-19.0`.
- **Publisher:** Overture Maps Foundation, <https://overturemaps.org/>.
- **Licence:** Community Data License Agreement — Permissive, version 2.0 (CDLA-Permissive-2.0), with
  Foursquare contributions under the Apache License 2.0 and AllThePlaces contributions under CC0 1.0.
- **Extract:** Italy, bounding box `6.6,35.4,18.6,47.1`, using Overture's Italy division polygon
  simplified to 0.002 degrees.
- **Contents:** 817,662 place records in 116 categories, built on 2026-09-23 (format version 2).

Records cite several contributing sources: Overture, Meta, Microsoft, PinMeTo, DAC, Overture-signals
and Krick under CDLA-Permissive-2.0; Foursquare under Apache-2.0; AllThePlaces under CC0-1.0. The
Overture places theme contains no OpenStreetMap data. The OpenStreetMap-derived works in this delivery
are the map archive and the routing graph, and they are credited separately.

The data was transformed for use by the application:

- restricted to the 116 categories the application serves;
- restricted to records whose coordinates fall inside Italy's national outline;
- restricted to records with a non-empty name and a confidence above zero;
- coordinates rounded to 1e-5 degrees (about 1.1 m);
- the confidence score retained as an integer scaled by 1000;
- the Overture identifier retained as its 16-byte value;
- the free-form address and locality joined into one display string;
- stored in a read-only SQLite table with an R-tree spatial index.

No attribute values were invented and no place was added. The Apache-2.0 NOTICE is retained in this
file for the Foursquare contributions.

The map displays the credit "Places data © Overture Maps Foundation (overturemaps.org) —
CDLA-Permissive-2.0 / Apache-2.0".

## Routing data — `routing-italy-3.9.0.tar.gz`

The archive contains a routing graph and the Valhalla engine.

### Routing graph

- **Source:** OpenStreetMap, Geofabrik regional extract of Italy (`italy-latest.osm.pbf`, SHA-256
  `218bed04f1667b12e2806136c9438f174b930f7536dc1368969b3271c14ebbe9`).
- **Publisher:** OpenStreetMap contributors.
- **Licence:** ODbL 1.0.
- **Copyright:** © OpenStreetMap contributors,
  <https://www.openstreetmap.org/copyright>.
- **Build:** Valhalla 3.9.0, built on 2026-09-25; 1,591 tiles in three levels (about 2.38 GB), plus an
  administrative database (about 22 MB). The graph is a Derivative Database under the ODbL.

The application displays "© OpenStreetMap contributors" on the map. A redistribution of the graph
must keep that attribution and comply with the ODbL, including its share-alike obligation.

### Valhalla engine

- **Project:** Valhalla, version 3.9.0, <https://github.com/valhalla/valhalla>.
- **Licence:** MIT.
- **Redistribution:** the compiled executables and shared libraries are unpacked from the `pyvalhalla`
  distribution published on PyPI. No Python code is included.

The MIT text is in `licenses/LICENSE-Valhalla-MIT.txt`.

The engine bundle also contains shared libraries from other projects: Abseil, FreeXL, GEOS, GeoTIFF,
iconv, libcurl, libexpat, libjpeg, liblzma, libtiff, libxml2, libzmq/czmq, Lua, LZ4, minizip, OpenSSL,
prime_server, PROJ, Protocol Buffers, SpatiaLite, SQLite, zlib and the Microsoft Visual C++ runtime.
Each library remains under its own licence — including MIT, BSD, Apache-2.0, LGPL, MPL and
public-domain terms — and its own copyright and permission notices apply. The authoritative texts are
published by each upstream project and by the `pyvalhalla` project; they are not reproduced in this
repository. For an LGPL-covered library, the corresponding source is available from that project's
public source repository.

## Changes to this file

When a release ships a different dataset, its release identifier, extract, row counts and build
metadata must be updated here in the same change. The data file carries its own `dataset_metadata`
table, and the routing archive carries `PROVENANCE.json`; those are authoritative for the exact
artifact.
