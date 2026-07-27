# Contributing Packs

A contribution should be a small, reviewable JSON pack. Prefer one theme or dimension per pack.

## Add Units To An Existing Dimension

Use a `units` pack when adding simple scalar units to a supported dimension:

```json
{
  "schemaVersion": "catverter.units/v1",
  "id": "example.kitchen.mass",
  "displayName": "Kitchen Mass Pack",
  "version": "1.0.0",
  "author": "Example Author",
  "description": "Adds kitchen-themed mass units.",
  "units": [
    {
      "id": "ceremonial-spoon",
      "dimension": "mass",
      "name": "Ceremonial spoon",
      "symbol": "ceremonial spoons",
      "emoji": "🥄",
      "singularName": "ceremonial spoon",
      "pluralName": "ceremonial spoons",
      "description": "A spoon promoted far beyond its natural authority.",
      "scientificNote": "Mass includes ceremonial expectations but excludes soup.",
      "origin": "Example kitchen standards desk",
      "baseFactor": 0.018,
      "tags": ["household", "tinyThings"]
    }
  ]
}
```

`baseFactor` is the amount of the dimension base unit represented by one funny unit. For mass this is kilograms, for length meters, for time seconds, and for temperature kelvin.

## Add Speed Ratio Units

Speed units reference existing length and time unit IDs:

```json
{
  "schemaVersion": "catverter.units/v1",
  "id": "example.speed",
  "displayName": "Example Speed Pack",
  "version": "1.0.0",
  "author": "Example Author",
  "description": "Adds speed ratio units.",
  "dependencies": [
    { "id": "catverter.core.length", "minVersion": "1.0.1" },
    { "id": "catverter.core.time", "minVersion": "1.0.1" }
  ],
  "ratioUnits": [
    {
      "id": "banana-per-tail-flick",
      "dimension": "speed",
      "numeratorUnitId": "banana",
      "denominatorUnitId": "tail-flick",
      "emoji": "🍌",
      "description": "A compact and mildly suspicious velocity.",
      "scientificNote": "Curvature is ignored again.",
      "origin": "Example speed desk",
      "tags": ["food", "cats"]
    }
  ]
}
```

## Add A Localization

Use `kind: "localization"` for translation-only packs. Localization packs should depend on the pack they translate and should not define units.

## Publish In This Repository

Place the pack under `contributions/<author-or-theme>/` and add an entry to `contributions/definitions.json`.
