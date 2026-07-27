# Catverter Packs

This repository is the public Catverter unit catalog.

## Layout

- `core/` contains official Catverter packs. These files are mirrored into the app as bundled offline content and are also used by the in-app core update flow.
- `contributions/` contains community packs and the contribution index used by the app.
- `schema/` contains JSON Schema files for pack authors and reviewers.
- `docs/` contains contributor guidance.

## Content Model

Core and contribution packs use the same JSON format. English text belongs in the main unit fields. Translated text belongs under `localizations`, for example `localizations.it`.

Keep unit IDs stable once published. If a unit needs a better display name, change `name`, `singularName`, `pluralName`, or a localization instead of changing `id`.

## Validation

Before publishing changes, validate JSON syntax and run the Catverter unit tests from the app repository. The app currently supports these dimensions in pack JSON:

- `mass`
- `length`
- `time`
- `temperature`
- `speed` ratio units
