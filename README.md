# Lunar Lander

A browser-based remake of the classic 1980s arcade **Lunar Lander**, built as a single self-contained HTML file with vanilla JavaScript and the HTML5 Canvas. Pilot a fragile lander down through gravity and limited fuel, and touch down gently on a scoring pad without crashing.

Styled as a green-phosphor vector terminal, it was created as a "Temark IT Easter egg."

**▶ Play it live:** https://powellga.github.io/Lunar_Lander/

## Gameplay

- You start each round at the top of the screen with a random horizontal position and drift, falling under constant gravity.
- Burn fuel to thrust and rotate, fighting gravity to line up a slow, level descent onto a landing pad.
- Land too fast, at too steep an angle, or off a pad, and you crash.
- Procedurally generated terrain and landing pads mean every round is different.

### Controls

| Input | Action |
|-------|--------|
| `↑` or `W` | Main thrust (in the direction the lander is pointing) |
| `←` / `→` or `A` / `D` | Rotate counter-clockwise / clockwise |
| `Space` | Start game / restart after landing or crashing |

### Scoring

Pads are color-coded by their point multiplier:

| Pad color | Multiplier |
|-----------|------------|
| Green | 1× |
| Cyan | 2× |
| Yellow | 3× |

A successful landing awards `1000 × multiplier + remaining fuel`, and the score accumulates across rounds.

### Landing rules

A touchdown only counts as a landing when **all** of these hold:

- The lander is over a landing pad.
- Combined speed is below the safe-landing threshold (`2` units/s).
- The tilt angle is under 15°.

Otherwise it's a crash. The HUD turns the H-Speed, V-Speed, and Fuel readouts red as a warning when they enter dangerous territory.

## How it works

Everything lives in `index.html` - markup, CSS, and game logic in one file.

- **Physics:** a fixed-step loop driven by `requestAnimationFrame` applies gravity each frame; thrust adds velocity along the lander's facing vector (`sin`/`cos` of its angle). The screen wraps horizontally.
- **Terrain & pads:** `generateTerrain()` walks left-to-right building a jagged ground polyline, randomly inserting flat landing pads (with random width and multiplier) along the way.
- **Collision:** `getAltitude()` interpolates the terrain height directly beneath the lander; when altitude reaches zero, `checkCollision()` decides landing vs. crash from speed, angle, and pad overlap.
- **Effects:** a lightweight particle system renders the engine plume during thrust and an explosion burst on impact; a static starfield sits behind the terrain.
- **HUD:** live readouts for score, fuel, altitude, and horizontal/vertical speed, with red warnings when unsafe.

### Tunable parameters

The constants near the top of the script are easy to tweak:

- `gravity` - downward acceleration per frame
- `maxSafeLandingSpeed` - crash threshold for impact speed
- `maxSafeLandingAngle` - crash threshold for tilt (degrees)
- per-round `fuel`, `thrustPower`, and `rotationSpeed` in `resetGame()`

## Running locally

No build step and no dependencies. Either:

- Open `index.html` directly in any modern browser, or
- Serve the folder over a static server, e.g. `python -m http.server`, then visit the page.

## Tech

- HTML5 Canvas 2D
- Vanilla JavaScript (no frameworks, no external assets)

## Author

Gregg Powell
