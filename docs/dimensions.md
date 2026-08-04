# Dimension Policy

Catverter dimensions are data-driven. Core dimensions and contributor dimensions use the same pack shape: a units pack may declare a top-level `dimensions` array, then add `units` or `ratioUnits` that reference those dimension IDs.

A pack can add units to a dimension when that dimension is either:

- declared in the same pack
- declared by an enabled dependency pack, including core packs such as `catverter.core.mass`

## Simple Dimensions

Use a simple dimension for scalar conversions where every input unit can convert to one base unit with:

```text
base value = input value * baseFactor + baseOffset
```

For ordinary linear units, omit `baseOffset` or set it to `0`. Temperature-style input units can use `baseOffset`, such as Celsius to kelvin.

Example dimensions that fit this model:

- `mass`
- `length`
- `time`
- `temperature`
- `volume`
- `area`
- `data-size`
- `energy`

## Ratio Dimensions

Use a ratio dimension when the output units are built from units in two other dimensions. Core `speed` is the first example: length over time.

A ratio dimension declares:

- `kind: "ratio"`
- `ratio.numeratorDimensionId`
- `ratio.denominatorDimensionId`
- optional default numerator and denominator input values/units for the app input UI

The `ratioUnits` entries then reference unit IDs from the numerator and denominator dimensions.

## Contributor Rules

A contributor can propose a new dimension by publishing a normal units pack that contains:

- at least one `dimensions` entry
- input units for that dimension
- at least one funny output unit, unless the pack only exists to define a dimension for other packs

A contributor cannot redefine a dimension ID that is already provided by an enabled core pack or another enabled contributor pack. Additional packs must depend on the dimension-providing pack and add units using that dimension ID.

For the first app-supported version of custom dimensions, prefer simple or ratio dimensions. Arbitrary formulas, live currency exchange, and other externally changing dimensions should wait for a later schema version.