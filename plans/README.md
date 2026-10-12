# Animation & Motion Plans

Implementation plans generated from the `/improve-animations` audit for Command Orb (`wonderful-mendeleev`).

## Plans Catalog

| # | Plan | Severity | Category | Status |
|---|---|---|---|---|
| [001](001-badge-entrance-scale.md) | Replace Scale Zero on Badge Appearance | **HIGH** | Physicality & origin | DONE |
| [002](002-calibrate-spring-durations.md) | Calibrate UI Spring Durations | **MEDIUM** | Easing & duration | DONE |
| [003](003-interruptible-tab-pulse.md) | Replace Keyframe Tab Pulse with Interruptible Active Transition | **MEDIUM** | Interruptibility | DONE |
| [004](004-consolidate-timing-tokens.md) | Consolidate Motion Timing Tokens | **LOW** | Cohesion & tokens | DONE |

## Recommended Execution Order

1. **Plan 002 (Calibrate UI Spring Durations)**: Sets base duration standards for snappy feedback across the UI.
2. **Plan 004 (Consolidate Motion Timing Tokens)**: Establishes shared `--dur-fast`, `--dur-base`, and `--ease-out` tokens.
3. **Plan 001 (Replace Scale Zero on Badge)**: Adopts token values to fix badge appearance pop.
4. **Plan 003 (Interruptible Tab Pulse)**: Cleans up DOM reflows on tab button droplet triggers.

## Dependencies

- Plan 001 and Plan 003 benefit from tokens introduced in Plan 002 and Plan 004.
