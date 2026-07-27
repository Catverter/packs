# Core Packs

Core packs are the official Catverter catalog.

Each core dimension lives in its own file:

- `catverter.core.mass.json`
- `catverter.core.length.json`
- `catverter.core.time.json`
- `catverter.core.temperature.json`
- `catverter.core.speed.json`

The app bundles these files for offline use and can check this folder for newer versions. Use semantic versions and bump a pack version whenever its public JSON changes.

## Localization Rule

The default fields should remain English. Localized names, descriptions, notes, origins, and variant text should live under `localizations`.

Example:

```json
{
  "name": "Standard cat",
  "singularName": "standard cat",
  "localizations": {
    "it": {
      "units": {
        "standard-cat": {
          "name": "Gatto",
          "singularName": "gatto"
        }
      }
    }
  }
}
```

## ID Rule

Do not rename published unit IDs unless the app also ships a migration. Existing IDs can be referenced by ratio units, saved settings, tests, and certificates.
