# ASCE 7 Wind Load Engine

A lightweight, dependency-free HTML prototype for preliminary ASCE 7-16 MWFRS wind load calculations.

The current app focuses on a low-rise office building workflow with live inputs, derived geometry, velocity pressure summaries, wall pressure tables, roof pressure tables, and base shear output. It is intentionally packaged as a single `index.html` file so users can open it directly, read the code, and make targeted edits without a build system.

## Quick Start

Open `index.html` in a browser.

No installation, package manager, backend, or internet connection is required.

## Current Scope

- ASCE 7-16 style preliminary wind load workflow
- Risk Category II prototype assumptions
- Exposure category B, C, or D
- Flat and gable roof cases
- Story-based wall pressure and force breakout
- Gable roof coefficient interpolation for the implemented prototype tables
- Light/dark theme support
- Single-file HTML/CSS/JavaScript architecture

## Important Disclaimer

This is an educational and prototype calculation aid, not a stamped engineering tool. Results must be independently verified against the governing ASCE standard, local code requirements, project-specific assumptions, and a qualified design professional.

## Repository Layout

```text
asce7_windload_engine/
  index.html
  README.md
  docs/
    ARCHITECTURE.md
    CALCULATION_ENGINE.md
    ASSUMPTIONS_AND_LIMITATIONS.md
    VERIFICATION_CHECKLIST.md
```

## Documentation

- [Architecture](docs/ARCHITECTURE.md)
- [Calculation Engine](docs/CALCULATION_ENGINE.md)
- [Assumptions and Limitations](docs/ASSUMPTIONS_AND_LIMITATIONS.md)
- [Verification Checklist](docs/VERIFICATION_CHECKLIST.md)

## Editing Philosophy

The app is designed to stay approachable. The calculation engine inside `index.html` is organized into labeled sections for state, constants, geometry, pressure helpers, roof coefficients, wall calculations, roof calculations, rendering, and event wiring.

When editing, prefer small changes in the relevant section instead of creating parallel calculation paths.
