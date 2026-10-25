# Cube

An interactive, keyboard-controlled 3D Rubik's Cube in a **single HTML file** (HTML + CSS + JavaScript), built with [Three.js](https://threejs.org/).

## Getting started

1. Save `cubo-rubik.html` on your computer.
2. Open it in a modern browser (Chrome, Firefox, Edge, Safari).

No installation or server needed. An internet connection is required, because Three.js (r128) and the fonts (Outfit, JetBrains Mono) are loaded from CDNs. Without the fonts, the browser falls back to system fonts.

## Controls

### Face turns (WCA notation)

| Key | Move |
|-----|------|
| `U` `D` `L` `R` `F` `B` | Turn a face **clockwise** (Up, Down, Left, Right, Front, Back) |
| `Shift` + letter | Turn a face **counter-clockwise** (e.g. `Shift + R` = R') |

### View

| Input | Action |
|-------|--------|
| Mouse or finger drag | Rotate the cube to see every face |
| `←` `→` `↑` `↓` | Orbit the camera around the cube |
| Mouse wheel / two-finger pinch | Zoom |
| Double click | Return to the default view |

### Other actions

| Input | Action |
|-------|--------|
| `Space` | Scramble the cube with 20 random moves |
| `Backspace` or `Esc` | Reset to the solved state |
| Button at the top right | Switch between dark and light theme |

> `R` turns the right face, so it can't also be used for reset.

## Features

- 3D cube made of 27 cubies with the classic colors (white, yellow, red, orange, green, blue) and black borders.
- Smooth face-turn animations (250 ms, eased). Moves pressed in quick succession are queued.
- Automatic scramble that never repeats the same face twice in a row.
- History of the latest moves at the bottom (e.g. `R U R' U'`).
- Dark and light theme, remembered by the browser.
- Works with keyboard, mouse and touch.

## Customization

The main constants are in the `CONFIGURAZIONE` section of the JavaScript code:

| Constant | Meaning |
|----------|---------|
| `COLORS` | Colors of the six faces |
| `MOVE_DURATION` | Duration of a turn (ms) |
| `SCRAMBLE_DURATION` | Duration of a turn while scrambling (ms) |
| `SCRAMBLE_LENGTH` | Number of moves in a scramble |
| `HISTORY_VISIBLE` | Number of moves shown in the history |
| `ISO_VIEW` | Initial camera angle |

The colors of the two themes are defined by the CSS variables at the top of the file (`:root` for dark, `[data-theme="light"]` for light).

## How it works

- Each turn attaches the cubies of the affected layer to a temporary pivot and rotates the pivot.
- When the animation ends, the cubies return to the main group and their position and orientation are rounded to avoid numerical drift.
- The camera orbits using spherical coordinates, with smooth interpolation toward target values.

## Tech stack

- HTML5, CSS3 (CSS variables, backdrop-filter)
- JavaScript (ES6+)
- Three.js r128
