# Places, selection and routes

## Selected places

`Selected places` appears at the top-left of the map once the list holds something.

- Each row carries a letter, the place's icon and name, and the town when the record has one.
- Press a row to move the camera back to that place.
- Press `✕` beside a row to remove that place; `Delete all` empties the list.
- The letter is a separate control: it starts a route.

The list is not saved. It is emptied when the application closes or when a plan or preset pin puts its
own places on the map. Replacing the place data removes any point you added from it.

## Routes between two selected places

1. Press the letter of the first place.
2. Press the letter of a different second place.
3. Choose how the group travels. The modes offered are the ones the routing engine can serve — normally
   `Car`, `Walking`, `Bicycle` and `Bus`. If no routing data is installed, the dialog says so and offers
   no mode.
4. Wait for the calculation, then choose how many routes to show: `1`, `2` or `3`.
5. Confirm to draw them.

Drawn routes appear on the map and in the `Routes` section below `Selected places`, fastest first. Each
journey has its own colour; slower alternatives are drawn fainter in the same colour.

- A row reads the start letter, the mode, the destination letter, the distance and the duration.
- The eye control shows or hides that line. Hiding changes the display only.
- `✕` removes one route; `Delete all` removes every route. There is no confirmation and no undo.
- A place that is the endpoint of a drawn route cannot be removed from `Selected places` until the
  route is removed. The one exception is blocking the place, which removes it, its row and every route
  that ends on it (see [Places you add and correct](#places-you-add-and-correct)).
- Routes are not saved and disappear when the application closes, when a plan or preset replaces the
  selection, or when a point they use is removed by a place-data replacement.

A route calculated here belongs to the selection. It is separate from the routes saved on a trip or
template composition, described in
[Templates, trips, presets and services](templates-trips-and-presets.md).

## Places you add and correct

There are two different things you can add from the map's right-click menu:

- **Add a point here** creates a temporary marker with a name and one of five icons. It joins
  `Selected places`, can be an endpoint of a route, and has no popup, category, address or contact
  details. It is not searchable and is removed when the place data is replaced; any route that used it
  is removed too.
- **Add a place here** creates your own place record at that location. It has a name, category,
  address and contact details, opens the normal popup, answers searches, can be linked to trips,
  templates and presets, and remains after a map or place-data replacement.

The `Edit` pencil on a place popup corrects an existing record in the same way. Your corrected version
then replaces the dataset's values on the map, in search results, in the popup and in the selected
list.

## Blocking a place

Blocking hides a place from the map, discovery and search without deleting anything. The only route is
the `Edit` form on a place popup: press `Block`, then confirm.

- The place stops being drawn and answered; its `Selected places` row and every route ending on it go.
- `Block` is unavailable while a preset contains the place or a saved composition places it on a day.
- A block survives a map or place-data replacement, keeping the name, category and position the
  `Records` panel shows. Nothing on the map marks one.
- `Restore` on its `Blocked` entry in [Records](#records) brings it back.

## Records

`Records` lists every place you have corrected, created or blocked.

- The field filters by name, town, address or category. The `Edited`, `Created` and `Blocked`
  checkboxes narrow by kind and combine with it; they are remembered until a restart.
- `Restore` on an edit returns the place to the dataset's values; `Delete` on a creation removes it.
- `Restore` on a block brings the place back and is never refused. It leaves a correction you also hold
  in place, and draws nothing if no data or record still describes the place.
- An edit or a creation is refused, with the reason, while a saved composition, a preset or a route
  depends on the place.

Records and blocks survive a map or place-data replacement and outlive the dataset that held the place.
