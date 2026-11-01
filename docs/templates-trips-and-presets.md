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
  and saved routes, and locks the day count. The end date is derived from the start date and the day
  count.
- **New preset** — asks only for a name.

Names are trimmed and must be unique within their kind; `Rome` and `rome` are the same name, and so
are `Àosta` and `aosta`. `Create` stays unavailable while a required field is invalid.

For a template or trip, `Edit` on a row opens a panel with the same fields. Saving a day count below
the last day that holds a place asks first, because the days above the new count and everything on
them are removed.

## The sidebar lists

- `Trips`, `Templates` and `Presets` each list their rows alphabetically, ignoring case and accents.
- `Search the list` filters the current tab by name.
- A row's pin puts its places on the map: they replace `Selected places` and the camera fits them. For
  a template or trip, its saved composition routes are drawn too. A place the current data no longer
  resolves is left out.
- The vertical-ellipsis button opens the row's actions.

## Composing a plan

Open `Composition` from a row's actions. The workspace replaces the map and shows linked places on the
left and the plan's days on the right.

1. **Link places.** Use the `Trips`, `Templates` or `Presets` tab of a place popup, or import a preset
   from the composition header. Importing a preset links its places in one action; the links survive
   `Discard changes` and create no placement.
2. **Place a linked place.** Drag its box into a day. Dropping on a day's empty area appends it; drop
   at a position to insert it. A place can be placed on several days, but not twice in neighbouring
   slots of the same day. The end of one day and the start of the next are allowed, so a hotel can be
   two consecutive nights.
3. **Move or remove instances.** Drag an instance within a day or to another day; `✕` removes that one
   instance and leaves the link and every other instance.
4. **Choose a transport mode for every gap.** Press the segment between two adjacent instances and
   choose `Car`, `Walking`, `Bicycle`, `Bus`, or `Unspecified`. With no routing data only `Unspecified`
   is offered.
5. **Assign services.** Press `+` on a placed occurrence and choose one of your services. The same
   service on two or more placements of one day is highlighted as a warning; it never blocks a save.
6. **Define routes.** `Define routes` in the header opens the routing workspace. Press a gap's row to
   ask the engine for alternatives, choose one, then `Save and return to the composition`. A route is
   stored on its gap and belongs to the mode it was calculated for; changing the mode hides it.
7. **Save.** `Save` writes the composition, its services and its routes. Leaving with unsaved changes
   asks first.

On a template, day headings read `Day 1` … `Day N`. On a trip they read the calendar date, with Italian
public holidays and Sundays in red and Saturdays in a softer red.

Unlinking a place is possible from the composition only while no day holds an instance of it; the
control asks first. A place held by a saved composition cannot be unlinked from a place popup either.

## Presets

A preset is a named shortlist of places for repeated use.

- Create one with `List actions → New preset`.
- `Show on the map` (the row's pin) puts its places into `Selected places` and fits the camera.
- `Edit` opens the preset's detail: rename it, review its places and remove one at a time.
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

Services are assigned only inside a composition, to a placed occurrence. They are not attached to a
place or to a plan's link list.
