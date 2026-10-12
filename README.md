# Adaptive Timeline

An exploration of mobile timeline UX featuring adaptive retention states, gesture-driven Command Orb physics, curved time horizons, and hardware-accelerated motion blur.

## Features

- **Adaptive Timeline Dial**: Curved time horizon calibrated with cubic-bezier geometry, dynamic segment highlights, and ambient horizon transitions.
- **5 Retention States**: Seamless exploration of Triage Horizon, Active Focus Session, Adaptive Reallocation, Silent Focus Room, Peak-End Climax, and Plan Overview.
- **Fluid Command Orb**: Interactive direct manipulation and spring gesture engine for natural language input and voice tasks.
- **Directional Motion Blur Engine**: Velocity-coupled anisotropic SVG blur filters with calibrated half-sine fade envelopes and GPU subpixel compositing.
- **Diagnostic Companion Sidebar**: Desktop live control panel with state switcher, pace simulator, interactive motion blur intensity slider, and wallpaper theme manager (OLED Pure Black, Silk Dark, Charcoal, Silk Light, Totoro).
- **Zero Build Dependencies**: Pure HTML, CSS, and vanilla JavaScript with zero external frameworks or build tooling.

## Quick Start

Open `index.html` directly in any modern browser, or run a local static server:

```bash
# Python
python3 -m http.server 8000

# Node.js
npx serve .
```

Then visit `http://localhost:8000`.

## Keyboard Shortcuts

- `1`: Triage Horizon
- `2`: Active Focus Session
- `3`: Adaptive Reallocation
- `4`: Silent Focus Room
- `5`: Peak-End Climax
- `6` / `P`: Plan Overview
- `B`: Toggle Motion Blur ON / OFF
- `Escape`: Dismiss Command Orb input
