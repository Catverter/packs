# Core Packs

Core packs are the official Catverter catalog.

Each core dimension lives in its own Italian definition file:

- `catverter.core.mass.json`
- `catverter.core.length.json`
- `catverter.core.time.json`
- `catverter.core.temperature.json`
- `catverter.core.speed.json`

Each English localization lives in a separate pack:

- `catverter.core.mass.en.json`
- `catverter.core.length.en.json`
- `catverter.core.time.en.json`
- `catverter.core.temperature.en.json`
- `catverter.core.speed.en.json`

The app bundles these files for offline use and can check this folder for newer versions. Use semantic versions and bump a pack version whenever its public JSON changes.

## Localization Rule

The default fields in unit packs should remain Italian. English names, descriptions, notes, origins, and variant text should live in `kind: "localization"` packs under `localizations.en`.

Example unit pack field:

```json
{
  "id": "standard-cat",
  "name": "Gatto",
  "singularName": "gatto"
}
```

Example English localization pack field:

```json
{
  "kind": "localization",
  "dependencies": [
    { "id": "catverter.core.mass", "minVersion": "1.0.2" }
  ],
  "localizations": {
    "en": {
      "units": {
        "standard-cat": {
          "name": "Standard cat",
          "singularName": "standard cat"
        }
      }
    }
  }
}
```

## Grammar Rule

Italian core units include `grammar.gender` so variants can render natural names. Variant packs should prefer adjective forms plus `{adjective}` / `{adjectivePlural}` patterns over phrases like `in versione`, for example `gatto alto`, `gatti alti`, `sedia alta`, and `sedie alte`.

English localization packs should keep their own `adjectiveForms` as `commonSingular` / `commonPlural` when the adjective does not change by gender or number.

## ID Rule

Do not rename published unit IDs unless the app also ships a migration. Existing IDs can be referenced by ratio units, saved settings, tests, and certificates.
