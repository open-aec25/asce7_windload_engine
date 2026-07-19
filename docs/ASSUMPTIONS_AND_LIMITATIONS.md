# Assumptions And Limitations

This project is a prototype and educational calculation aid. It is not a substitute for the ASCE standard, local code review, project-specific engineering judgment, or a stamped design.

## Current Assumptions

- ASCE 7-16 prototype scope
- Risk Category II
- Exposure category B, C, or D
- Directionality factor `Kd = 0.85`
- Topographic factor `Kzt = 1.0`
- Ground elevation factor `Ke = 1.0`
- Gust effect factor `G = 0.85`
- Internal pressure coefficient `GCpi = +/-0.18`
- Enclosed building
- Rigid structure
- Flat and gable roof scope

## Known Limitations

- The app is not validated as a production engineering tool.
- Flat roof roof-zone behavior is simplified.
- Gable roof pressure coefficients are implemented only for the current prototype scope.
- Hip, monoslope, mansard, and other roof families are out of scope.
- Dual orthogonal wind direction analysis is not automatic.
- Project-specific topographic, enclosure, importance, and jurisdictional requirements must be reviewed separately.
- Gable roof surface area should be reviewed where sloped surface area differs from projected plan area.

## Intended Use

Use this prototype to explore calculation flow, UI behavior, data organization, and preliminary wind load concepts. Do not use it as the sole basis for engineering design.
