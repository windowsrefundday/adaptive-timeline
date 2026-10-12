# 001 - Replace Scale Zero on Badge Appearance

- **Status**: TODO
- **Commit**: b6f1c67
- **Severity**: HIGH
- **Category**: Physicality & origin
- **Estimated scope**: 1 file (`index.html`), ~10 lines

## Problem

In `index.html`, the task count badge uses `transform: scale(0)` to hide when count is zero. Nothing in physical reality scales from absolute zero dimensions; this creates a popping artifact rather than an organic entrance.

```css
/* index.html:241-243 - current */
.badge { min-width: 18px; height: 18px; padding: 0 5px; border-radius: 999px; font-size: 11px; font-weight: 600; line-height: 18px; font-variant-numeric: tabular-nums; background: var(--ink); color: var(--bg); transform: scale(0); transition: transform var(--apple-snappy-dur) var(--apple-snappy); }
.seg button.on .badge { background: var(--accent-ink); color: var(--accent); }
.badge.show { transform: scale(1); }
```

## Target

The badge must enter from `scale(0.85)` with `opacity: 0` using a quick fade-in coupled to the snappy Apple spring scale, settling naturally without disappearing into a point singularity.

```css
/* target */
.badge {
  min-width: 18px; height: 18px; padding: 0 5px; border-radius: 999px;
  font-size: 11px; font-weight: 600; line-height: 18px; font-variant-numeric: tabular-nums;
  background: var(--ink); color: var(--bg);
  opacity: 0; transform: scale(0.85); pointer-events: none;
  transition: opacity 160ms cubic-bezier(0.23, 1, 0.32, 1), transform var(--apple-snappy-dur) var(--apple-snappy);
}
.seg button.on .badge { background: var(--accent-ink); color: var(--accent); }
.badge.show { opacity: 1; transform: scale(1); pointer-events: auto; }
```

## Repo conventions to follow

- Spring curve: `var(--apple-snappy)` defined in `:root`.
- Fast opacity ease: `cubic-bezier(0.23, 1, 0.32, 1)`.

## Steps

1. Open `index.html`.
2. Locate the `.badge` and `.badge.show` rules around line 241.
3. Update `.badge` to include `opacity: 0`, `transform: scale(0.85)`, and dual transition (`opacity 160ms ease-out, transform var(--apple-snappy-dur) var(--apple-snappy)`).
4. Update `.badge.show` to include `opacity: 1; transform: scale(1); pointer-events: auto;`.

## Boundaries

- Do NOT change the DOM structure of `<span class="badge">`.
- Do NOT alter badge font sizing or padding.

## Verification

- **Mechanical**: Open `index.html` in browser, verify no CSS syntax errors.
- **Feel check**:
  - Add a new task via voice or mock text that increments the badge count on the inactive tab.
  - Confirm the badge emerges softly from 85% scale and fades in, with no popping singularity.
- **Done when**: `.badge` transitions from `opacity: 0; transform: scale(0.85)` to `opacity: 1; transform: scale(1)`.
