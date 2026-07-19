# Architecture

This project is a single-page, dependency-free HTML application.

The app is intentionally kept in one file:

```text
index.html
```

That file contains:

- Markup for controls and result sections
- CSS for layout, responsive behavior, and theme variables
- JavaScript for state, calculations, SVG preview rendering, tables, and event wiring

## User Interface Organization

The interface uses a two-column application layout:

- Left sidebar: live controls for roof type, wind speed, exposure, geometry, stories, gable settings, and custom floor heights
- Right results pane: visual preview, equations, coefficient cards, velocity pressure cards, wall table, roof table, base shear summary, and notes

The sidebar is sticky on desktop so users can adjust inputs while viewing results.

## JavaScript Organization

The script is divided into labeled sections:

1. Application state and engineering constants
2. Theme and general UI helpers
3. Wind pressure helpers
4. Input normalization and geometry
5. Roof coefficient data and interpolation
6. Visual preview rendering
7. Roof zone calculations
8. Calculation model
9. Wall and base shear calculations
10. Result rendering
11. Central orchestration
12. Event wiring

The central `calc()` function is deliberately short. It builds one calculation model, calculates wall rows, calculates roof rows, calculates base shear, and sends those results to the rendering functions.

## Design Goal

The code should be readable by engineers, educators, and advanced users who may want to audit or modify the assumptions. The organization favors explicit named functions over hidden framework behavior.
