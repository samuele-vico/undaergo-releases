# Troubleshooting

## Windows says the publisher is unknown

The installer is not code-signed. Choose **More info**, then **Run anyway**. Verify the file's SHA-256
against the checksum list supplied with the release if you want to confirm it was not altered.

## The application starts with an empty map

That is the first-run state: Undaergo ships without data. Open `Data` and import the map file first,
then the place file, then the routing archive. See
[Installation and first data import](installation.md).

## The place import refuses to run

A place import reads the map to obtain town and street names, so it requires a map. Install the map
first, then import the places.

## The place import asks about a category

The dataset contains a category the application has not seen before. Review its name, count and
examples, then choose the application category it belongs to, or exclude it. The application never
guesses.

## Places do not appear on the map

- Expand the layers rail and switch on at least one category.
- Zoom in. A view larger than one search is refused with `Zoom in to load places.`
- Lower `Minimum confidence` in `Settings`; records below the threshold are not shown.
- If no place data is installed, `Data` says so.
- The place may be blocked: nothing on the map marks a block. Look for a `Blocked` entry in `Records`.

## A search answers nothing

- The query must hold at least four characters before any comma.
- At least one search chip must be on.
- If a search area is drawn, results are limited to it. Remove the polygon and search again.
- A comma restricts the rest of the query to one town: `via roma, firenze`.
- A blocked place never answers. Restore it from `Records` and search again.

## The Block control is unavailable

`Block` needs the place to be in no preset and on no day of a saved composition. Remove it from those,
save, then block it from the place's `Edit` form. A plan link alone does not prevent a block.

## A blocked place does not come back after Restore

`Restore` forgets the block; the place reappears only if the installed place data or a correction of
yours still describes it. Otherwise the entry can be restored but there is nothing left to draw.

## Export to Word

- **Missing entry** — only a trip has one: `Trips` → row's vertical-ellipsis button.
- **`No Word templates`** — put a `.docx` directly in `<installation folder>\resources\word-templates`
  and reopen the window. The folder is named in full; writing to it may need administrator rights.
- **Trust question** — the template's commands run as code. `Export anyway` remembers that exact file
  content; editing the file asks again.
- **Export fails** — usually the template names something the document does not carry. The window keeps
  the chosen template; fix the file against `GUIDE.md` and try again. Nothing is written on failure.

## Route calculation is unavailable

- The dialog says `No road network is available` when no routing graph is installed. Import
  `routing-*.tar.gz` from `Data`.
- The composition's mode picker offers only `Unspecified` for the same reason.
- An archive built for a different engine version is refused by name. Use the archive supplied with
  this release of the application.

## An import is slow or seems stopped

Map and place imports can take minutes; the routing archive is large and takes longer. The panel
reports its step and can be closed while the work continues. If the import is cancelled or fails, the
previous dataset remains in use.

## An import refuses for lack of disk space

The `Data` panel reports the space an import requires against the space available, and refuses rather
than half-installing. Free space, then try again. Once all three datasets are imported, the folder the
files came in can be deleted; it takes about 4.6 GiB. See
[Installation and first data import](installation.md#can-i-delete-the-folder-the-data-came-in).

## I need to start over

First back up `%APPDATA%\Undaergo` if you may want the data later. Deleting that folder resets the
application: it removes trips, templates, presets, services, place records, preferences, the trusted
Word template record and every imported dataset. Deleting only `%APPDATA%\Undaergo\data` removes the
imported datasets and keeps the operator database.

## Reporting a problem

Open an issue at <https://github.com/samuele-vico/undaergo-releases/issues> and include:

- the application version, as it appears in the installer file name (for example
  `Undaergo-1.0.1-setup.exe`);
- the names and sizes of the data files you imported;
- the exact message the application showed;
- what you did immediately before the problem.
