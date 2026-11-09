# Installation and first data import

## Requirements

- 64-bit Windows 10 or later.
- About 12 GB of free disk space while the datasets are imported and the folder they arrived in still
  exists; about 5 GB once that folder is deleted (see
  [Can I delete the folder the data came in?](#can-i-delete-the-folder-the-data-came-in)).
- No internet connection. The application never downloads map, place or routing data.

## Install the application

1. Download `Undaergo-<version>-setup.exe` from the **Releases** page of this repository.
2. Run the installer. It installs for the current user and lets you choose the installation folder.
3. The installer is not code-signed. If Windows SmartScreen says the publisher is unknown, choose
   **More info**, then **Run anyway**.
4. Start **Undaergo** from the Start menu or the desktop shortcut.

The application starts without any data: the map is empty and the `Data` panel says
`No data is installed yet.` This is the normal state on a new installation.

## Import the data

The map, place and routing files are distributed separately from the installer. Obtain them from your
supplier and keep them together in one folder.

1. Open **Data** in the toolbar.
2. Choose **Choose a map file (italy.pmtiles)**, select `italy.pmtiles`, review the inspection, then
   choose **Install this map**.
3. Choose **Choose a place file (.sqlite)**, select `poi-overture.sqlite`, review the inspection and
   the category mapping it proposes, then choose **Import this data**.
4. Choose **Choose a routing file (routing-*.tar.gz)**, select the routing archive exactly as supplied,
   review the inspection, then choose **Install this routing data**.

The order matters for the first two. The place import reads the map to obtain town and street names,
so it refuses to run without a map. The routing import is independent and can be done at any time.

- The map import copies the archive, which takes seconds on a fresh installation. Replacing a map
  while place data is installed also rebuilds the place and street names from the new archive, and
  that takes minutes; the map in use stays on screen until the new one is in place.
- The place import takes minutes.
- The routing import takes minutes: the archive holds about fifteen hundred files and the application
  unpacks it itself. Do not extract it first; hand the `.tar.gz` file to the application.
- A running import can be cancelled. The `Data` panel may also be closed while the work continues;
  reopen it with **Data** to see the progress.

The application is usable while a dataset is missing. Search and discovery need place data, route
calculation needs routing data, and the place import needs a map.

## Can I delete the folder the data came in?

Yes, once all three imports have finished. The application reads each file and copies what it needs
into its own folder under `%APPDATA%\Undaergo\data`; it never reads the supplied files again.

- **Delete the folder** to get back the space it takes (about 4.6 GiB with the current datasets).
  The application keeps its own copies and is unaffected.
- **Keep it** if you may need to re-import later: the data is not downloadable from this repository,
  and a re-import needs the original files. Keeping it also lets you reinstall the datasets after
  resetting the application.
- **Do not delete it while an import is running, or after one failed or was cancelled.** A cancelled
  or failed import installs nothing, and the supplied file is then the only copy of what you were
  given.

Deleting the folder does not remove what the application has already imported. To remove that, see
[Where your data lives](data-records-settings.md#where-your-data-lives).

## Disk space

The application keeps its own copy of each dataset, so every import needs room for that copy and, while
it runs, for a temporary copy beside it. Before an import starts, the `Data` panel reports the space it
requires against the space available, and refuses rather than half-installing.

| What | Size |
| --- | --- |
| Installed application | about 400 MB |
| Map | 2.1 GiB |
| Place database | 0.2 GiB supplied; the installed dataset adds the street and place names swept from the map |
| Routing network | 2.2 GiB of tiles plus 21 MiB of administrative boundaries |
| The data folder you were given | about 4.6 GiB |

The previous place dataset is kept on disk so that `Revert` stays available, so replacing the places
holds two of them. The map and routing replacements keep no previous copy, but a routing import needs
room for the old and the new network at the same time.

## Word templates

`Export to Word` reads `%APPDATA%\Undaergo\word-templates`. The export window creates the folder the
first time it opens and copies the sample `.docx` and `GUIDE.md` into it. Copy your own `.docx` files
there — only files directly in the folder are listed. It needs no administrator rights, and the
installer, an update and the uninstaller never touch it, so your templates stay. Never add a template
you do not trust: its commands run as code.

See [Exporting a trip to Word](templates-trips-and-presets.md#exporting-a-trip-to-word). `Export to Word`
is a PRO feature: see [Licence](#licence).

## Update the application

Run a newer installer over the existing installation. It replaces the application and its routing
engine and leaves the operator database and the imported datasets untouched. Your Word templates live
under `%APPDATA%` and are kept as they are. The same is true of the uninstaller: it removes the
application, not your data.

## Uninstall

Use **Settings → Apps → Installed apps → Undaergo → Uninstall**. The operator database, preferences,
Word templates and imported datasets remain in `%APPDATA%\Undaergo`. To remove them too, delete that
folder after uninstalling; this also deletes your trips, templates, presets and place records.
Uninstalling removes the application folder only.

## Licence

The application is proprietary and works without a licence, except for its two PRO features:
`Export to Word` and `Assign shortest routes`. Both wear a crown while no PRO licence is active, and
pressing one opens the `Licence` window. Enter the key from your supplier once; the heading then reads
`PRO licence active` and `Valid until <date>`. A lapsed licence reconnects and renews from the computer's
own record — open `Licence` and press `Retry`. Nothing you have entered, drawn or exported is taken
away by a licence state.

## Verify the files you received

If your supplier provides a `checksums.sha256` list, verify each file before importing it:

```powershell
Get-FileHash -Algorithm SHA256 .\italy.pmtiles
```

Compare the result with the matching line. A file that does not match was damaged in transfer; ask for
it again instead of importing it.

## Licences installed with the application

The installation carries every third-party notice and licence text in its `licenses` folder, and
`Settings → Licences → Open the licence folder` opens it. The map, place and routing files you import
keep their own licences — the Open Database License 1.0, CDLA-Permissive-2.0 and Apache-2.0 — and are
not covered by the application licence. See [Third-party notices](../THIRD-PARTY-NOTICES.md).
