# 002 - Calibrate UI Spring Durations

- **Status**: TODO
- **Commit**: b6f1c67
- **Severity**: MEDIUM
- **Category**: Easing & duration
- **Estimated scope**: 1 file (`index.html`), ~15 lines

## Problem

In `index.html:36-42`, the duration tokens for the calibrated Apple springs are set too long for high-frequency interactive UI:
`--apple-morph-dur: 0.67s;` (670ms) and `--apple-snappy-dur: 0.54s;` (540ms).
UI animations must stay under 300-450ms; at >500ms, repeated interactions (tab switching, arriving tasks, day selection) feel sluggish and slow to settle.

```css
/* index.html:36-42 - current */
--apple-morph-dur: 0.67s;
--apple-snappy-dur: 0.54s;
--apple-smooth-dur: 0.49s;
```

## Target

Calibrate the duration tokens so the linear spring curves resolve promptly within the UI response budget:

```css
/* target */
--apple-morph-dur: 0.42s;
--apple-snappy-dur: 0.32s;
--apple-smooth-dur: 0.36s;
```

## Repo conventions to follow

- Duration tokens are declared at `:root` alongside `--apple-morph`, `--apple-snappy`, `--apple-smooth`.
- The linear spring curves have settling tails; reducing the duration token tightens the active motion phase without clipping the subtle settle.

## Steps

1. In `index.html`, locate the `:root` block lines 35-43.
2. Change `--apple-morph-dur: 0.67s;` to `--apple-morph-dur: 0.42s;`.
3. Change `--apple-snappy-dur: 0.54s;` to `--apple-snappy-dur: 0.32s;`.
4. Change `--apple-smooth-dur: 0.49s;` to `--apple-smooth-dur: 0.36s;`.

## Boundaries

- Do NOT alter the `linear(...)` keyframe curve definitions.
- Do NOT change the JavaScript physics engine parameters in `springTo` (`stiffness = 320; damping = 30`).

## Verification

- **Mechanical**: Reload page, verify CSS variables are applied.
- **Feel check**:
  - Switch tabs between Todo and Calendar; the sliding capsule indicator `.seg-ind` should settle crisply in ~300ms without feeling delayed.
  - In DevTools Animations panel at 25% speed, verify the settle remains smooth.
- **Done when**: All CSS spring transitions resolve within 420ms.
