# 004 - Consolidate Motion Timing Tokens

- **Status**: TODO
- **Commit**: b6f1c67
- **Severity**: LOW
- **Category**: Cohesion & tokens
- **Estimated scope**: 1 file (`index.html`), ~20 lines

## Problem

Throughout `index.html`, multiple CSS rules use hardcoded transition durations and easings:
- Line 275: `.check { transition: background .35s ease, transform var(--apple-snappy-dur) var(--apple-snappy); }`
- Line 276: `.check i { transition: opacity .25s ease, transform var(--apple-snappy-dur) var(--apple-snappy); }`
- Line 282: `.t-title { transition: color .4s ease; }`
- Line 298: `.day { transition: background .4s ease, color .4s ease, transform var(--apple-snappy-dur) var(--apple-snappy); }`
- Line 364: `.sheen { transition: opacity .4s ease; }`

These hardcoded values drift over time and create inconsistent pacing across list items, checkboxes, and buttons.

## Target

Define reusable timing tokens at `:root` in `index.html`:
```css
/* target tokens */
--ease-out: cubic-bezier(0.23, 1, 0.32, 1);
--dur-fast: 160ms;
--dur-base: 240ms;
--dur-settle: 360ms;
```
Replace scattered literal durations with these semantic tokens.

## Repo conventions to follow

- Tokens live in `:root` alongside color and material variables.
- Fast interactive changes (hover, press, opacity) use `--dur-fast`.
- Layout state changes use `--dur-base` or `--dur-settle`.

## Steps

1. In `index.html:43`, add the timing tokens:
   `--ease-out: cubic-bezier(0.23, 1, 0.32, 1);`
   `--dur-fast: 160ms;`
   `--dur-base: 240ms;`
2. Update `.check` transition to use `--dur-base` and `--ease-out`.
3. Update `.check i` opacity transition to use `--dur-fast`.
4. Update `.t-title` color transition to use `--dur-base`.
5. Update `.day` color and background transitions to use `--dur-base`.

## Boundaries

- Do NOT change the spring definitions or physics engine.
- Only replace hardcoded timing literals with the new tokens.

## Verification

- **Mechanical**: Inspect computed styles of `.check`, `.day`, `.t-title` to verify tokens are active.
- **Feel check**:
  - Click checkboxes on task list items: checkmark appears crisply with snappy tactile feedback.
  - Click days on the calendar: background color shifts cleanly at 240ms.
- **Done when**: No bare `.35s ease` or `.4s ease` transitions remain on high-frequency UI elements.
