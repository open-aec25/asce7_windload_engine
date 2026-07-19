# Calculation Engine

The calculation engine follows a simple pipeline:

```text
User inputs -> Calculation model -> Wall and roof calculations -> Rendered results
```

## Constants And Exposure Parameters

Fixed wind constants are grouped in `WIND_CONSTANTS`:

- `Kd`
- `Kzt`
- `Ke`
- `G`
- `GCpi`

Exposure parameters are grouped in `EXPOSURES` for Exposure B, C, and D. The selected exposure category controls the `alpha` and `zg` values used by the velocity pressure coefficient calculation.

## Geometry

The geometry helpers convert user-friendly architectural inputs into calculation geometry:

- `getStoryHeights()`
- `getDerivedGeometry()`
- `getRoofHeightData()`
- `getFloorElevations()`

The app keeps architectural building length and width visually stable, then derives ASCE `L` and `B` based on wind direction and ridge orientation.

## Velocity Pressure

The pressure helpers are:

- `getExposureParams(exposure)`
- `getKz(h, exposure)`
- `getQz(z, V, Kzt, Kd, Ke, exposure)`

`getKz()` applies the 15 ft minimum evaluation height for the exposure coefficient.

The app distinguishes:

- `qh` at ASCE height `h`
- `qz` at eave or story-top height
- story-specific `qz` values used by windward wall rows

## Wall Calculations

Wall rows are generated story by story.

Each story includes:

- Windward wall
- Leeward wall
- Side wall - left
- Side wall - right

Windward wall pressure uses story-specific `qz` for the external pressure term. Leeward and side wall pressures use `qh`.

Base shear is summarized from windward and leeward wall forces only. Side wall rows are displayed for visibility but are not added into the one-direction base shear summary.

## Roof Calculations

Roof pressure logic is routed through `getRoofZones()`.

Current roof families:

- Flat roof
- Gable roof

Gable roof coefficient logic uses tabulated prototype constants, sign-aware interpolation, area reduction where flagged, and governing net-pressure selection using both internal pressure signs.

Flat roof zones remain simplified prototype values.

## Rendering

Calculation functions return data objects. Rendering functions consume those objects and update the DOM:

- Coefficient cards
- Velocity pressure cards
- Wall pressure table
- Roof pressure table
- Base shear cards
- SVG preview

This separation keeps calculation logic easier to inspect and edit.
