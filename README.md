# ✨ Magic Charms

A touch-first, iOS-playable **match-3 charm-swapping puzzle game** — a single
self-contained HTML file with no dependencies, no build step, and no network
requests. Open `index.html` in any browser (it's tuned for iPhone Safari) and
play.

## 🎮 How to play

- **Swipe** (or tap-then-tap an adjacent tile) to swap two charms.
- Line up **3 or more** matching charms to clear them and score.
- Cleared charms rain down replacements — chain **cascades** multiply your score.
- Reach the **goal score** before your **moves** run out to clear the level.
  Each level raises the goal.

### Power-ups

| Match | Creates | Effect |
|---|---|---|
| 4 in a row | ⬅➡ / ⬆⬇ Striped charm | Clears its whole row / column when matched |
| 5 in a row, or an L/T shape | 🔮 Magic orb | Swap it with any charm to wipe every charm of that color |
| Orb + Orb | 💥 | Clears the entire board (+2000) |

Best score and current level are saved locally (`localStorage`), so progress
survives closing the tab.

## 📱 Playing on iPhone

1. Host the repo with any static server (e.g. enable **GitHub Pages** on this
   branch, or run `python3 -m http.server` and open it on your phone), or just
   AirDrop / open the file.
2. Open the page in Safari.
3. Optional: **Share → Add to Home Screen** — the game installs like an app,
   full-screen with no Safari chrome (it ships the `apple-mobile-web-app`
   meta tags, safe-area insets, and touch handling for a native feel).

## 🛠 Tech notes

- Pure vanilla JS + a single `<canvas>` renderer (60 fps `requestAnimationFrame`
  loop, devicePixelRatio-aware).
- Swap tweens, gravity-based falling, pop/particle effects, floating score text.
- Sound effects synthesized live with the Web Audio API (no audio files);
  audio unlocks on first touch as iOS requires.
- Board logic: run detection, special spawning (striped / orb), chain-reaction
  removal expansion, dead-board detection with auto-reshuffle.
- Smoke-tested headlessly with Playwright (board integrity, valid/invalid swap
  behavior, cascade resolution, level flow).
