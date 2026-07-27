# Dimension Policy

Catverter currently supports contributor units for these dimensions:

- `mass`
- `length`
- `time`
- `temperature`
- `speed` ratio units, built from length over time

A new kind of unit, such as volume, area, pressure, data size, or currency, needs app support before ordinary packs can use it. Until the runtime supports custom dimensions, contributors should propose the dimension first instead of publishing packs that use unsupported dimension IDs.

## New Dimension Proposal

A proposal should include:

- dimension ID, such as `volume`
- display name
- base unit, such as liter or cubic meter
- expected SI/base conversion rule
- at least three example input units
- at least three funny output units
- whether the dimension is simple linear, offset-based, or composite

For the first app-supported version of new dimensions, prefer simple linear scalar dimensions. Composite dimensions can follow later once the runtime and UI have a stable model.

## Future Pack Shape

Future dynamic dimensions should live beside their units in the pack that introduces them, rather than in a separate repository. Packs that merely add units to an existing dimension should reference that dimension ID.
