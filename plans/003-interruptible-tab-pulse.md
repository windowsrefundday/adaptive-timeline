# 003 - Replace Keyframe Tab Pulse with Interruptible Active Transition

- **Status**: TODO
- **Commit**: b6f1c67
- **Severity**: MEDIUM
- **Category**: Interruptibility
- **Estimated scope**: 1 file (`index.html`), ~15 lines

## Problem

In `index.html:239-240`, the tab button pulse uses `@keyframes tabPulse`:
```css
/* index.html:239-240 - current */
.seg button.pulse { animation: tabPulse var(--apple-snappy-dur) var(--apple-snappy); }
@keyframes tabPulse { 0% { transform: scale(1); } 35% { transform: scale(1.05); } 100% { transform: scale(1); } }
```
In JavaScript line 727, restarting this animation on droplet arrival requires a forced layout reflow hack:
```js
el.classList.remove('pulse'); void el.offsetWidth; el.classList.add('pulse');
```
Forced synchronous reflows (`offsetWidth`) block the rendering pipeline. Keyframes cannot retarget mid-flight if multiple items arrive rapidly.

## Target

Replace `@keyframes tabPulse` with a CSS transition driven by a transient `.bounce` class or clean scale transition that retargets smoothly without forcing synchronous layout recalculations:

```css
/* target */
.seg button {
  /* ... */
  transition: color .24s ease, transform 180ms cubic-bezier(0.23, 1, 0.32, 1);
}
.seg button:active, .seg button.pulse {
  transform: scale(0.94);
}
```
And in JS droplet finish, simply toggle the class with a timeout or let the active state handle tactile feedback.

## Repo conventions to follow

- Press feedback: `transform: scale(0.94-0.96)`.
- Duration: 160-200ms with fast ease-out.

## Steps

1. In `index.html`, locate `.seg button.pulse` and `@keyframes tabPulse`.
2. Remove `@keyframes tabPulse`.
3. Update `.seg button` transition to `transition: color .24s ease, transform 180ms cubic-bezier(0.23, 1, 0.32, 1);`.
4. Update `.seg button.pulse` to `transform: scale(1.06);`.
5. In `launchDroplets()` line 727, remove `void el.offsetWidth;` and use `requestAnimationFrame` to trigger the pulse class if needed.

## Boundaries

- Do NOT alter droplet trajectory calculation or droplet DOM elements.
- Keep `.seg-ind` indicator transition untouched.

## Verification

- **Mechanical**: No `offsetWidth` calls in `launchDroplets`.
- **Feel check**:
  - Dispatch a task with 3-4 items.
  - Watch the tab icons receive items without any frame hitching or layout thrashing.
- **Done when**: Droplet arrival triggers smooth icon pulse with zero forced synchronous layout reflows.
