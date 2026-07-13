# Clocktower data

`scripts.json` is the manifest. Each entry points to a role catalog and a
`scriptFile`. Files in `data/scripts/` use the same JSON format exported and
imported by https://script.bloodontheclocktower.com/: an optional `_meta`
object followed by character IDs or full homebrew character objects. `aliases`
maps official IDs to this app's canonical IDs.

Each file in `roles/` is an array of role objects:

```json
{
  "id": "washerwoman",
  "name": "Washerwoman",
  "team": "Townsfolk",
  "first": {
    "order": 33,
    "action": "Wake the Washerwoman.",
    "detail": "Show a Townsfolk token..."
  },
  "other": null
}
```

- `first` and `other` are independent night instructions.
- Use `null` when a role has no instruction in that phase.
- `order` is the canonical global night-order position.
- `action` must explicitly say who wakes. Storyteller-only actions should say
  that the role resolves without waking.
- Add a role ID to its Script Tool file as well as its role catalog.

Script Tool `_meta.firstNight` and `_meta.otherNight` arrays are honored when
present, including the `minioninfo` and `demoninfo` positions. Without explicit
orders, the canonical order numbers in the role catalogs are used.

The browser validates required fields, duplicate IDs, night instructions, and
missing manifest references before rendering the app.
