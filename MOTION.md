# rd motion spec (draft 1)

The animations are in `animations.json` and `svg-animated/`.

## Principles

1. **Animation is opt-in and an overlay.** The static icon never changes. An icon only moves when someone asks for it (`animate` in React, the animated SVG on the website).
2. **It must mean something.** Motion explains the icon: a bell rings, an arrow drops into its tray, a lock snaps shut. No decoration for its own sake.
3. **Small and soft.** Movements are a few pixels or degrees, never bouncy cartoons.
4. **Every animation starts and ends at the resting icon.** No "forwards" end states, so there is no jump when it stops, and it can loop.
5. **One signature move.** Container icons (folder, mail, calendar, window, image, save, card, terminal, home) **close their open corner**, settle with a small press, then open again. This is the rd signature.
6. **Respect people.** Everything is wrapped in `prefers-reduced-motion: no-preference`. With "reduce motion" on, icons stay still.

## Timing

| | |
|---|---|
| Duration | 0.5 to 0.95 s per play (set on each icon); one number, `--rd-speed`, scales all of them (`2` = twice as slow, `0.5` = twice as fast) |
| Easing | `cubic-bezier(.34, 1.3, .5, 1)` (soft overshoot) for things that land; `ease-in-out` for swings and spins; `linear` for loaders |
| Stagger | 0.06 to 0.12 s between parts that move one after another (sliders, wifi) |
| Repeat | once per trigger; `loop` repeats forever |

## Vocabulary (what each kind of icon does)

| Kind | Motion |
|---|---|
| Containers (signature) | corner closes, shape presses (scale .95 then 1.03), corner opens |
| Things that ring or swing (bell) | rotate around the hanging point, decaying |
| Things that land (download) | move 2.5 px along the arrow, rebound |
| Things that turn (settings, sun, plus, close, star, refresh) | rotate by the symmetry angle so the end pose equals the start pose |
| Things that draw (check, check-circle) | the stroke draws on |
| Things that count (clock, wifi, sliders) | parts move in sequence |

## Triggers (the `animate` prop)

| Value | When it plays |
|---|---|
| `"hover"` (or `true`) | the icon itself is hovered |
| `"parent"` | the icon's parent element is hovered (for example a button) |
| `"play"` | while set; change it away and back to replay |
| `"loop"` | continuously (loading states) |

## Technical rules

- Pure CSS in an inline `<style>` that ships with the icon; no JavaScript, no extra files.
- Every rule is scoped to the icon's own class (`.rd-a-<name>`), so two icons never affect each other.
- Animate `translate`, `rotate`, `scale`, `opacity`, `stroke-dashoffset` and `stroke-dasharray` only (cheap and broadly supported).
- The resting look of the animated drawing must equal the static drawing (checked in the build).
- No more than 4 animated parts per icon.
