# Curvature Visualiser

Interactive explorations of the differential geometry of plane curves — watch osculating circles track along parametric curves, see curvature and evolutes unfold in real time.

### [Launch App](https://brendanjameslynskey.github.io/Curvature_Visualiser/)

---

## What is this?

Curvature measures how fast a curve is turning at each point. At any point on a smooth plane curve, there is a unique circle — the **osculating circle** — that best approximates the curve locally. Its radius is the reciprocal of the curvature, R = 1/κ, and its centre lies on the normal to the curve at a distance R. Where the curve bends tightly, the osculating circle is small; where it is nearly straight, the circle becomes enormous.

The locus of all these centres as you sweep along the curve is called the **evolute** — a companion curve with its own elegant geometry. The evolute is also the envelope of the normal lines to the original curve, and it typically has cusps at points where the curvature of the original curve has a local extremum.

This app lets you explore these ideas interactively. Select from 12 parametric curves, adjust their parameters, and watch the osculating circle glide along the curve while the evolute traces out beside it. Two companion plots show κ(t) and R(t) as functions of the parameter. Applications range from road design (the clothoid provides a linear curvature transition for comfortable driving) to optics (caustics are evolutes of wavefronts), roller coaster engineering, and the study of curves in differential geometry.

## Curves

| Curve | Description |
|-------|-------------|
| **Circle** | Constant curvature — the osculating circle is the curve itself, and the evolute degenerates to a single point (the centre) |
| **Ellipse** | Curvature varies smoothly between a²/b and b²/a at the vertices; the evolute is an astroid |
| **Lissajous** | Superposition of two sinusoidal motions — adjustable frequency ratio and phase create figures-of-eight, knots, and complex loops |
| **Cardioid** | A limaçon with a cusp at the origin; curvature is unbounded at the cusp, and the evolute is a smaller cardioid |
| **Limaçon** | Generalisation of the cardioid — an inner loop appears when b > a, creating regions of sign-changing curvature |
| **Astroid** | A hypocycloid with four cusps where curvature diverges; the evolute is a larger astroid rotated 45° |
| **Epicycloid** | A circle rolling outside another circle — adjustable radii R and r control the number of cusps |
| **Lemniscate of Bernoulli** | A figure-of-eight; curvature passes through zero at the self-intersection, making the osculating circle flip orientation |
| **Archimedean Spiral** | Constant spacing between turns; curvature decreases monotonically as the spiral unwinds |
| **Logarithmic Spiral** | Self-similar — the osculating circle at every point subtends the same angle, giving constant curvature-to-arc-length ratio |
| **Clothoid (Euler spiral)** | Curvature varies linearly with arc length — used in highway and railway design for smooth transitions between straight and curved segments |
| **Catenary** | The curve of a hanging chain under gravity; curvature peaks at the lowest point and decays exponentially |

## Mathematical Background

For a parametric curve (x(t), y(t)):

- **Curvature:** κ = |x'y'' − y'x''| / (x'² + y'²)^(3/2)
- **Radius of curvature:** R = 1/κ
- **Osculating circle centre:** C = (x − y'(x'²+y'²)/(x'y''−y'x''), y + x'(x'²+y'²)/(x'y''−y'x''))
- **Evolute:** the locus of C as t varies
- **Unit normal:** (−y', x') / |(−y', x')|

Analytical derivatives are used where possible; finite differences are used for curves defined via integrals (Clothoid, Lemniscate).

## Features

- **12 parametric curves** with adjustable parameters via sliders
- **Osculating circle** drawn at a moveable point along the curve, updating in real time
- **Curvature-coloured curve** — blue for low curvature, red for high curvature
- **Evolute overlay** shown as a dashed companion curve
- **Unit normal vector** displayed as an arrow at the current point
- **Two companion plots** — κ(t) and R(t) vs parameter, with a vertical marker at the current position
- **Play/pause animation** with speed control (0.25× to 4×)
- **Manual parameter slider** for precise positioning along the curve
- **Live info panel** — current coordinates, κ, R, tangent angle, and parameter value
- **Equal-aspect-ratio axes** so circles actually look circular
- **Pan, zoom, and scroll** on all plots (Plotly.js)
- **Responsive dark-theme UI**

## Built with

- [Plotly.js](https://plotly.com/javascript/) for interactive plotting
- Vanilla HTML/CSS/JS — no build step, no dependencies to install
