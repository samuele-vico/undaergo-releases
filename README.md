# Undaergo

Undaergo is a Windows desktop application for group-travel operators: it draws an offline vector map of Italy, searches places, streets and businesses, discovers places and lodgings from the current map view, calculates car, walking, bicycle and bus routes, and composes reusable templates and dated trips day by day with places, services and saved routes. Places you never want to see can be blocked and restored from the `Records` panel, and a trip can be exported as a Word document through the templates supplied with the installation or added by you. The application ships without data: the map, place database and routing network are supplied separately and imported from the `Data` panel; search, discovery and routing remain unavailable until the corresponding file has been imported.

## Install

1. Download `Undaergo-<version>-setup.exe` from this repository's **Releases** page and run it. The installer is not code-signed, so Windows SmartScreen shows an unknown publisher: choose **More info**, then **Run anyway**. The application installs for the current user.
2. Obtain the data files that accompany the release from your supplier: `italy.pmtiles` (map), `poi-overture.sqlite` (places) and `routing-italy-<engine-version>.tar.gz` (road network). They are distributed separately and are not contained in the installer or in this repository.
3. Start Undaergo and open **Data** in the toolbar. Choose and install the map first, then the place file, then the routing archive. The place import reads the map, so it refuses without one; routing can be imported at any time.
4. Wait for each import to finish. A first map import takes seconds; a later one also rebuilds the place and street names and takes minutes. The place and routing imports take minutes, and the panel may be closed while they continue.

Once all three imports have finished, the folder the data files came in can be deleted: the application keeps its own copies. Keep it if you may need to re-import later. See [Installation and first data import](docs/installation.md#can-i-delete-the-folder-the-data-came-in).

## Manual

- [Installation and first data import](docs/installation.md)
- [Map, search and discovery](docs/map-and-search.md)
- [Places, selection and routes](docs/places-and-routes.md)
- [Templates, trips, presets and services](docs/templates-trips-and-presets.md)
- [Data, records and settings](docs/data-records-settings.md)
- [Troubleshooting](docs/troubleshooting.md)

## Licence

The Undaergo application is proprietary software, free of charge for personal and internal business use; see [LICENSE](LICENSE). The map, place and routing data keep their own licences — Open Database License 1.0, CDLA-Permissive-2.0 and Apache-2.0 — and are not covered by the application licence; see [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) and the [licence texts](licenses/).
