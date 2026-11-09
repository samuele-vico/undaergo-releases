# Map, search and discovery

## The window

- **Left:** the `Trips`, `Templates` and `Presets` tabs, with `Search the list` and `List actions` on
  the tab bar. Drag the divider to resize the panel.
- **Centre:** the map. A place popup opens on it when you point at or select a place.
- **Right:** the layers rail, collapsed to icons until you expand it. It holds the basemap overlays and
  the place-category switches.
- **Top:** the search button and the search-area polygon button.
- **Bottom:** the toolbar: the `Licence` key at the far left, separated from `Data`, `Records`,
  `Services` and `Settings`.
- **Over the map:** `Selected places`, the `Routes` list and the panels opened from the toolbar or a
  plan.

Only one toolbar surface is open at a time; opening another closes the previous one.

## Moving the map

- Drag to pan, use the wheel or a pinch to zoom, or use the two zoom buttons in the top-right corner.
- The arrow keys pan; `+` and `-` zoom.
- The camera stays inside Italy and cannot zoom out past the whole country.
- **Themes:** `Liberty — Flat map` is north-up and draws buildings as outlines. `3D — Tilted view with
  extruded buildings` allows tilt and rotation. The control is below the zoom buttons.
- **Label language:** switch between `EN` and `IT` beside the map. A name stays Italian when the data
  has no English name for it, which is usual for street names.
- **Overlays:** expand the layers rail to switch on `Railways` (from zoom 6) and `Ferries` (from zoom
  11). Both start off.

## The map's right-click menu

Right-clicking the map's own drawing opens a menu at that point:

- **Add a place here** — opens the place form at that location and creates a place that belongs to
  you: it can be searched, edited and linked to plans, and it survives a data replacement.
- **Add a point here** — asks for a name and one of five icons. The point is a map marker for the
  current session: it has no category or contact details, opens no popup, is not searchable, and is
  removed when the place data is replaced.
- **Copy map as image** — copies the visible map, including its credits and any points you added, to
  the clipboard. Panels and controls are not included.

A short red flash marks the point the menu acts on. Right-clicking a place, a pin or a map control does
not open this menu.

## Searching

Press the magnifier in the header. Type at least four characters; results appear a moment after you
stop typing. Up to twenty results are listed.

The chips choose what answers:

| Chip | Answers with |
| --- | --- |
| `Towns and cities` | Cities, towns, villages, hamlets and provincial capitals |
| `Regions` | The Italian regions |
| `Street names` | Named streets |
| `Places and businesses` | Categorised places |
| `Districts and localities` | Neighbourhoods, suburbs, quarters and named localities |
| `Lakes and rivers` | Lakes, rivers, islands, bays and straits |

With `Places and businesses` on, eight further chips narrow the categories: places to stay, food and
drink, outdoors, culture, places of worship, public transport, fuel / parking and taxis, practical.

- Put a comma after the phrase to restrict the search to one town: `via roma, firenze`.
- Choosing a street, town, region, district or water moves the camera to it.
- Choosing a categorised place also adds it to `Selected places`.
- A place you have blocked is never answered: not listed, nothing it holds matches. Restoring it on the
  `Records` panel makes it answer again.
- `Escape` closes the search and clears the query.

### Searching inside a drawn area

The polygon button beside the search button draws an area on the map:

1. Press the button, then click at least three points on the map.
2. Press the first point again to close the polygon. `Escape` or a second press on the button abandons
   the trace.

While the area stands, typed searches answer only with entities inside it and the status line says so.
The area is captured when each search is formed; removing it does not re-run the last search. The area
cannot be edited: remove it and draw another.

## Discovering places on the map

Expand the layers rail and switch on one or more categories:

- `Places to stay`
- `Food and drink`
- `Outdoors`
- `Culture`
- `Places of worship`
- `Public transport`
- `Fuel, parking & taxis`
- `Practical`

The application searches the visible view and draws matching places with their names. Panning or
zooming asks for the newly visible area. A view too large for one search is refused with
`Zoom in to load places.` rather than searched in part.

- Switching a category off removes its places at once.
- A place you have blocked is never drawn, counted or answered, under any category or chip. Nothing
  marks its absence; the area simply reads as though the place were not in the data. See
  [Records](places-and-routes.md#records).
- Places that would overlap are shown as a badge with a count; press it to zoom in until they separate.
- The `Minimum confidence` setting decides which records are shown. Lowering it includes less certain
  records; see [Data, records and settings](data-records-settings.md).

## Place details

Pointing at or pressing a place opens one popup with four tabs:

- **Info** — category, address, website, phone, email and social links held by the record.
- **Trips**, **Templates**, **Presets** — the operator's own plans and shortlists, each with a control
  that links or unlinks this place. A link adds the place to that plan or preset; it does not place it
  on a day.

The `Select` pin adds the place to `Selected places`. On a categorised place, the `Edit` pencil opens
the place form and saves your own version of its name, category, address and contacts. A corrected
place reads as your version everywhere; taking the correction back is done from the `Records` panel.

The edit form also carries `Block`, which hides the place from the map and the search without deleting
anything; its `Selected places` row and every route ending on it go too. A block is refused while a
preset contains the place or a saved composition places it on a day, is never marked on the map, and is
taken back from the `Records` panel. See [Records](places-and-routes.md#records).

The map's credits line is always visible and names the place-data provider, MapLibre and the
OpenStreetMap contributors separately.
