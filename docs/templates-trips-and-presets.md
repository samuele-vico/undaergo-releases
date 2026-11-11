# Templates, trips, presets and services

## Templates and trips

A **template** is the reusable shape of a trip: a name, a description, a number of days, the places it
holds and a composition of days and places. It has no date.

A **trip** is a dated plan: a name, a description, a start date, a number of days, a participant count
and its own composition. A trip can be created empty or copied whole from a template; after creation
the two are independent, and deleting the template does not change the trip.

Both are saved in the application's database and survive updates, map replacements and place-data
replacements.

## Creating one

Use `List actions` on the sidebar tab bar:

- **New template** — asks for `Name`, `Description` and `Days`.
- **New trip** — asks for `Name`, `Description`, an optional template, `Days`, `Start Date` and
  `Participants`. Choosing a template fills `Days` from it, copies its places, composition, services
  (on places and on days) and saved routes, and locks the day count. The end date is derived from the
  start date and the day count.
- **New preset** — asks only for a name.

Names are trimmed and must be unique within their kind; `Rome` and `rome` are the same name, and so
are `Àosta` and `aosta`. `Create` stays unavailable while a required field is invalid.

For a template or trip, `Edit` on a row opens a panel with the same fields. Saving a day count below
the last day that holds a place asks first, because the days above the new count and everything on
them are removed.

## Cloning one

**PRO feature.** `Clone` in a row's actions opens a window titled `Clone preset`, `Clone template` or
`Clone trip`, with `Name` prefilled as `Copy of <name>`.

The copy is exact: every linked place, and for a template or trip the whole composition — placements,
services on places and days, transport modes and saved routes; a trip also keeps its dates, status,
participants and source template. Only the name and the new identifier differ. `Cancel`, `Escape` and a
press outside the window close it and create nothing; a name already in use is refused.

## The sidebar lists

- `Trips`, `Templates` and `Presets` each list their rows alphabetically, ignoring case and accents.
- `Search the list` filters the current tab by name.
- A row's pin puts its places on the map: they replace `Selected places` and the camera fits them. For
  a template or trip, its saved composition routes are drawn too. A place the current data no longer
  resolves is left out.
- The vertical-ellipsis button opens the row's actions. A trip lists `Edit`, `Composition`, `Clone`,
  `Export`, `Export to Word`, `Delete`; a template lists the same without `Export to Word`; a preset
  lists `Edit`, `Clone`, `Export`, `Delete`. `Clone` and `Export` are PRO features and wear a crown
  while no licence is active; `Export` writes a `.undaexp` file, while `Export to Word` writes a
  document. See [Exporting and importing files](export-and-import.md).

## Composing a plan

Open `Composition` from a row's actions. The workspace replaces the map and shows linked places on the
left and the plan's days on the right.

1. **Link places.** Use the `Trips`, `Templates` or `Presets` tab of a place popup, or add a preset's
   places from the composition header. Adding a preset links its places in one action; the links
   survive `Discard changes` and create no placement.
2. **Place a linked place.** Drag its box into a day. Dropping on a day's empty area appends it; drop
   at a position to insert it. A place can be placed on several days, but not twice in neighbouring
   slots of the same day. The end of one day and the start of the next are allowed, so a hotel can be
   two consecutive nights.
3. **Move or remove instances.** Drag an instance within a day or to another day; `✕` removes that one
   instance and leaves the link and every other instance.
4. **Choose a transport mode for every gap.** Press the segment between two adjacent instances and
   choose `Car`, `Walking`, `Bicycle`, `Bus`, or `Unspecified`. With no routing data only `Unspecified`
   is offered.
5. **Assign services.** Press `+` on a placed occurrence, or on a day's header, and choose one of your
   services. A day's services belong to the day and not to any place on it. The same service twice in
   one day — on the day and its places, or on two placements — is highlighted as a warning; it never
   blocks a save.
6. **Calculate the shortest routes in one click.** `Assign shortest routes` in the header fills every
   segment that has a transport mode with the shortest route by distance, in a single run. Choose at
   least one mode first. It works on unsaved changes; when some segments already hold a route it asks
   whether to keep those or replace them. **PRO feature.**
7. **Define routes.** `Define routes` in the header opens the routing workspace. Press a gap's row to
   ask the engine for alternatives, choose one, then `Save and return to the composition`. A route is
   stored on its gap and belongs to the mode it was calculated for; changing the mode hides it.
8. **Save.** `Save` writes the composition, its services and its routes. Leaving with unsaved changes
   asks first.

On a template, day headings read `Day 1` … `Day N`. On a trip they read the calendar date, with Italian
public holidays and Sundays in red and Saturdays in a softer red.

Unlinking a place is possible from the composition only while no day holds an instance of it; the
control asks first. A place held by a saved composition cannot be unlinked from a place popup either.

## Exporting a trip to Word

**PRO feature.** Only a trip has a Word export; the entry wears a crown while no PRO licence is
active. It is a different entry from `Export`, which writes a `.undaexp` data file.

1. Row actions → `Export to Word`. The document describes the **saved** composition, not unsaved edits.
2. Choose a template. The dropdown lists the `.docx` files in `%APPDATA%\Undaergo\word-templates` by
   name, A→Z, first chosen; the folder is read on each opening. `.docm`, `.dotx` and subfolders are
   ignored. With none, the window says `No Word templates` and names the folder.
   `Settings → Folders → Open the Word templates folder` opens that folder directly.
3. A template whose commands are new to the application asks first: they run as code, so continue only
   if you trust the file. `Export anyway` remembers that exact content — an edited file asks again.
4. `Export` opens a Save dialog suggesting `<trip name>.docx`, then writes one document: commands
   replaced by the trip's data, styles, headers, footers, images and tables kept as authored. A failure
   keeps the window and the chosen template open; nothing is written.

The document carries the trip's fields, every day with its own services and its places in walking
order, each with its category and services, every leg, and the tallies by service, category and mode.
Dates are ISO unless the template formats them. An export changes nothing else.

The export window, or `Settings → Folders → Open the Word templates folder`, creates that folder with
the sample template and `GUIDE.md` on first use. It is yours: adding, editing or deleting a template
needs no administrator rights, and installing, updating or uninstalling the application never touches
it.

## Presets

A preset is a named shortlist of places for repeated use.

- Create one with `List actions → New preset`.
- `Show on the map` (the row's pin) puts its places into `Selected places` and fits the camera.
- `Edit` opens the preset's detail: rename it, review its places and remove one at a time.
- `Clone` and `Export` copy it, inside the application or to a `<name>.undaexp` file; both are PRO.
- `Delete` removes the preset and its links; the places themselves are untouched.
- A place that the current data no longer holds stays in the preset, marked
  `No longer in the place data`, until you remove it.

A preset feeds the map selection, the composition import and the place popup's `Presets` tab. It is not
changed by those surfaces.

## Services

Open `Services` in the toolbar. The panel has two tabs:

- **Services** — your catalogue of what the group buys. `New service` asks for:
  - `Code` — exactly five characters from `A`–`Z` and `0`–`9`, unique;
  - `Name` — unique;
  - `Type` — one of the shipped service types;
  - `Description`.

  Rows can be searched, sorted, edited and deleted. A service held by a saved composition cannot be
  deleted until the last reference is removed and saved.
- **Service types** — the read-only vocabulary shipped with the release. Each type has a name and a
  definition. Types cannot be created, renamed or deleted; a new release can add, rename or withdraw
  one without changing the trips that already name a service.

Services are assigned only inside a composition: to a placed occurrence, or to a whole day. They are
not attached to a place or to a plan's link list. A service held by a day blocks its deletion exactly
as one held by a placement does.
