# RRAC events

The event list the WorkoutTracker app downloads for its **Events** tab. Edit `events.json` and commit; the app picks up changes the next time it refreshes (GitHub's CDN can take a few minutes).

> The events here to start with are **samples**. Replace them with real ones.

## Fields

| Field | Required | Notes |
|---|---|---|
| `id` | yes | Unique and stable. Don't reuse; the app uses it to remember completed challenges. |
| `kind` | yes | `club`, `challenge` or `competition` |
| `title` | yes | |
| `details` | no | Free text. |
| `starts` | yes | `2026-12-01` for an all-day date, or `2026-12-12T10:00:00-05:00` for a time (include the UTC offset). |
| `ends` | no | Same formats. Date-only means *through the end of that day*. Defaults: same day for all-day dates, two hours after a timed start. |
| `location` | no | `{ "name": "…", "latitude": 40.7, "longitude": -74.0 }`. Coordinates are optional; without them the map searches by name. |
| `link` | no | Signup/info URL. Shown as a button. |
| `goal` | challenges | `{ "movement": "pushUps", "reps": 1000 }` or `{ "workouts": 12 }`. Movements: `dips`, `pullUps`, `pushUps`, `australianRows`. |

Challenge progress is counted on each member's phone from the workouts they log inside the `starts`–`ends` window.

Keep `"version": 1` at the top. It only changes if the format does.
