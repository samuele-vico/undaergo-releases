# Data, records and settings

## The Data panel

Open `Data` in the toolbar. It reports what the application is running on:

- the place dataset: how many places and streets it holds, which release it came from, when it was
  built, and whether it carries contact details;
- the map: where it is, its size, its deepest zoom and whether it was installed by you;
- the routing network: whether a graph is installed and which engine built it;
- your own records: how many places you have created or corrected, kept separate from the dataset's
  figures.

When nothing is installed, the panel says so and lists the import order.

### Replacing the map

1. Choose `Choose a map file (italy.pmtiles)`.
2. The file is inspected before anything is written: its zoom range and any problem are reported.
3. If it can be used, choose `Install this map`.

Installing a map also rebuilds the place and street names, because the application reads them from the
map file — but only when place data is already installed. On a first run the map is simply copied, and
the names are built by the place import that follows. The map replacement leaves places you added to
the map standing; it does not touch the place dataset.

### Replacing the place data

1. Choose `Choose a place file (.sqlite)`.
2. The file is inspected: release, build date, rows, categories and how many rows would be imported or
   skipped.
3. A category the application has not seen before is never guessed. For each one, review its name, its
   count and some examples, then say which kind of place it is or that it should not be imported.
4. Choose `Import this data`.

Replacing the place data removes points you added to the map, silently, and removes any route that used
one. Your corrections, your created places, your presets, your templates and your trips are kept. A
correction whose place the new dataset no longer holds continues as your own place.

After an import, the panel compares the new dataset with the previous one. The previous place dataset
is kept and can be restored from the panel after review and confirmation; restoring affects only place
data, never the map.

### Installing the routing network

1. Choose `Choose a routing file (routing-*.tar.gz)`.
2. Keep the archive as supplied; do not extract it.
3. Review the inspection and choose `Install this routing data`.

The engine accepts only an archive built for its own version; an archive for a different version is
refused by name. Routes work as soon as the archive is unpacked, with no restart. The previous graph
keeps working until the new one is complete.

### While an import runs

The panel reports the current step and its progress where the work can be counted. The import can be
cancelled, and the panel can be closed while it continues. Reopen `Data` to see it again.

## Records

`Records` lists every place you have corrected, created or blocked.

- The field filters by name, town, address or category, never by a contact detail. The `Edited`,
  `Created` and `Blocked` checkboxes narrow by kind and combine with it.
- `Restore` on an edit returns the place to the dataset's values; `Delete` on a creation removes it.
- `Restore` on a block brings the place back and is never refused.
- An edit or a creation is refused, with the reason, while a saved composition, a preset or a route
  depends on the place.

All three survive a map or place-data replacement. Blocking is reached only from a place's `Edit` form
and is never marked on the map; see
[Places, selection and routes](places-and-routes.md#blocking-a-place).

## Settings

`Settings` holds the preference that decides which place data is shown:

- `Minimum confidence` — a slider; below the value a place is not discovered on the map. Lowering it
  shows more places, including less certain ones; raising it leaves them out.
- A preview reports how many places in the current view the value would yield and how far from the
  centre they reach. It counts food and drink and places to stay only.
- `Save` stores the value. The map uses it immediately; the value survives a restart.

The panel states the file where the preference is stored.

### Licences

`Settings` also carries a `Licences` section. `Open the licence folder` opens the directory installed
beside the application, which holds every third-party notice and licence text: the software the
application is built on, the libraries the routing engine loads, the map's glyphs and icons, and the
map, place and routing datasets. `NOTICE-bundle.txt` in that folder names each component and where its
terms are. See [Third-party notices](../THIRD-PARTY-NOTICES.md).

## Where your data lives

Everything the operator owns is under `%APPDATA%\Undaergo`:

- the database with trips, templates, presets, services and place records;
- the settings file;
- the `word-templates` folder with your Word templates, created on the first export;
- the record of Word templates you have already trusted, so an export does not ask again;
- the imported map, place database and routing graph under `data\`.

The installer, an update and the uninstaller do not touch this folder. Deleting it manually resets the
application to a first-run state and removes all operator data.
