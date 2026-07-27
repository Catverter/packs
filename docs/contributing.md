# Contributing Packs

A contribution should be a small, reviewable JSON pack. Prefer one theme or dimension per pack.

Catverter unit packs use Italian as the canonical language. Add English or other translations with separate `kind: "localization"` packs.

## Add Units To An Existing Dimension

Use a `units` pack when adding simple scalar units to a supported dimension:

```json
{
  "schemaVersion": "catverter.units/v1",
  "id": "example.kitchen.mass",
  "displayName": "Massa da Cucina",
  "version": "1.0.0",
  "author": "Example Author",
  "description": "Aggiunge unità di massa a tema cucina.",
  "units": [
    {
      "id": "ceremonial-spoon",
      "dimension": "mass",
      "name": "Cucchiaio cerimoniale",
      "symbol": "cucchiai cerimoniali",
      "emoji": "🥄",
      "singularName": "cucchiaio cerimoniale",
      "pluralName": "cucchiai cerimoniali",
      "description": "Un cucchiaio promosso ben oltre la sua autorità naturale.",
      "scientificNote": "La massa include aspettative cerimoniali ma esclude la zuppa.",
      "origin": "Banco standard cucina di esempio",
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
  "displayName": "Velocità di esempio",
  "version": "1.0.0",
  "author": "Example Author",
  "description": "Aggiunge unità di velocità a rapporto.",
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
      "description": "Una velocità compatta e lievemente sospetta.",
      "scientificNote": "La curvatura viene ignorata di nuovo.",
      "origin": "Banco velocità di esempio",
      "tags": ["food", "cats"]
    }
  ]
}
```

## Add English Text

Use `kind: "localization"` for translation-only packs. Localization packs should depend on the pack they translate and should not define units.

```json
{
  "schemaVersion": "catverter.units/v1",
  "kind": "localization",
  "id": "example.kitchen.mass.en",
  "displayName": "English Localization - Kitchen Mass Pack",
  "version": "1.0.0",
  "author": "Example Author",
  "description": "English localization for the kitchen mass pack.",
  "dependencies": [
    { "id": "example.kitchen.mass", "minVersion": "1.0.0" }
  ],
  "localizations": {
    "en": {
      "displayName": "Kitchen Mass Pack",
      "description": "Adds kitchen-themed mass units.",
      "units": {
        "ceremonial-spoon": {
          "name": "Ceremonial spoon",
          "symbol": "ceremonial spoons",
          "singularName": "ceremonial spoon",
          "pluralName": "ceremonial spoons",
          "description": "A spoon promoted far beyond its natural authority.",
          "scientificNote": "Mass includes ceremonial expectations but excludes soup.",
          "origin": "Example kitchen standards desk"
        }
      }
    }
  }
}
```

## Publish In This Repository

Place the pack under `contributions/<author-or-theme>/` and add an entry to `contributions/definitions.json`.
