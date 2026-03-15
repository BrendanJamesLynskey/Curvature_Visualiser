# Curvature Visualiser

**[Launch App](https://brendanjameslynskey.github.io/Curvature_Visualiser/)**

An interactive, browser-based tool for exploring the differential geometry of parametric curves. Visualise osculating circles, curvature plots, evolutes, and normal vectors in real time.

## Curves

| Curve | Equation | Parameters |
|---|---|---|
| Circle | x = cos t, y = sin t | -- |
| Ellipse | x = a cos t, y = b sin t | a, b |
| Lissajous | x = sin(at + d), y = sin(bt) | a, b, d |
| Cardioid | r = a(1 + cos t) | a |
| Limacon | r = a + b cos t | a, b |
| Astroid | x = a cos^3 t, y = a sin^3 t | a |
| Epicycloid | (R+r)cos t - r cos((R+r)t/r), ... | R, r |
| Lemniscate of Bernoulli | r^2 = a^2 cos 2t | a |
| Archimedean Spiral | r = at | a |
| Logarithmic Spiral | r = a e^(kt) | a, k |
| Clothoid (Euler Spiral) | Fresnel integrals | a |
| Catenary | x = t, y = a cosh(t/a) | a |

## Features

- Osculating circle at a moveable point along the curve
- Curvature kappa(t) and radius of curvature R(t) plots
- Evolute (locus of centres of curvature) overlay
- Unit normal vector display
- Play/pause animation with adjustable speed
- Adjustable curve parameters via sliders
- Information panel with live numerical readouts
- Dark theme with responsive layout

## Mathematics

For a parametric curve (x(t), y(t)):

- **Curvature:** kappa = |x'y'' - y'x''| / (x'^2 + y'^2)^(3/2)
- **Radius of curvature:** R = 1 / kappa
- **Osculating circle centre:** C = (x - y'(x'^2+y'^2)/(x'y''-y'x''), y + x'(x'^2+y'^2)/(x'y''-y'x''))
- **Evolute:** locus of C as t varies
- **Normal vector:** (-y', x') / |(-y', x')|

Analytical derivatives are used where possible; finite differences are used for curves defined via integrals (Clothoid, Lemniscate).

## Built With

- [Plotly.js](https://plotly.com/javascript/) for interactive plotting
- Vanilla HTML / CSS / JavaScript
- GitHub Pages for hosting
