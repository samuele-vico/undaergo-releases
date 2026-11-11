# Exporting and importing files

`Export` writes one preset, template or trip to a `.undaexp` file; `Import` reads such files back on
the same or another installation. Both are **PRO features**, and both wear a crown while no PRO
licence is active.

A `.undaexp` file is a plain-text data file, not a document to read and not a map, place or routing
dataset. It holds one entity whole: its identifier, name, description (and, for a trip, dates, status,
participants and source template), every linked place with its record and point, the saved composition
with its day services, routes and modes, and the services themselves.

## Exporting one

1. Open the row's vertical-ellipsis button and choose `Export`.
2. The Save dialog suggests `<name>.undaexp`; a name typed without the extension receives it.
3. `Save` writes one file and changes nothing else. Cancelling writes nothing and says nothing; a
   refusal is shown briefly above the list.

The file describes the **saved** composition: unsaved edits are not exported. Exporting the same
unchanged entity twice writes identical content. A preset's file carries its links only, as a preset
has no composition. See [Cloning one](templates-trips-and-presets.md#cloning-one) for a copy that stays
inside the application instead of becoming a file.

## Importing files

`Import` sits last in `List actions`, in every tab. It opens a three-step window.

### Step 1 — choosing files

- Drop files on the window or use `Choose files`. Only names ending with `.undaexp` are taken, at most
  five files per batch and 32 MB each; a file already in the list is not added twice.
- `Remove` takes a chosen file out before advancing. `Next` reads the files.

### Step 2 — what the files hold

Nothing is written yet. Each file is read on its own: a file that cannot be used is named with its
reason and the rest continue.

For every usable file the window names its kind, its name, whether it `will be created` or
`will be overwritten`, and what it carries — places, and for a template or trip services and days.
Overwriting replaces the entity whole: name, places, composition, services and routes, so local changes
the file does not hold are lost. `Back` returns to the file list and discards the reading.

### Step 3 — writing

`Import` writes one file at a time. Each file is written in one go: a refusal anywhere rolls that file
back, the files before it stay imported and the files after it still run. The report names each file's
outcome and ends `<n> files imported.` or `<n> imported, <m> failed.` The window cannot be closed while
it runs; `Close` ends it once the last file has answered. Imported entities appear in the sidebar
immediately.

### What an import decides

- **The file's identifier is the update key.** An identifier this installation already holds for the
  same kind is updated in place; a new one is created with the file's identifier. An identifier held by
  another kind refuses the file.
- **A name another entity already holds refuses the file** and nothing of it is written. Template and
  trip names are unique per kind; preset names are unique across all presets.
- **Services are matched by code.** A code this installation already holds is reused and the composition
  points at it; a missing code creates a service. A service name already used under a different code
  refuses the file.
- **A place already reading the same is left alone**; a different one, or one this installation does
  not hold, is written into your own place records, never into the place dataset.
- **A file written by an older version carries no place details**: its places import when this
  installation already resolves them, otherwise the file is refused.
- **A trip keeps its source template** only when this installation holds that template; otherwise it
  imports with no provenance.
- A file is refused while a `Data` import is running, because a suspended place dataset would read
  every place as absent.

A refused file leaves the database as it was: no partial file, no half-written entity. There is no
choice per file of what to keep — the file replaces, or it is refused. See
[Troubleshooting](troubleshooting.md#a-undaexp-file-is-refused).
