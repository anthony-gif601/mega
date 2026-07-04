# 🍀 Magic Charms

A faithful, touch-first clone of **Magic Charms**, the chain-link puzzle from
Megatouch bar-top arcade machines — rebuilt as a single self-contained HTML
file tuned for iPhone Safari. No dependencies, no build step, no network.

## 🎮 How to play

- Tap a charm, then tap another charm of the **same style** to chain them.
- A charm can join the chain only if it's reachable from the last one by a
  path through empty dirt cells with **two or less turns** — the link is drawn
  as a glossy blue tube, and chained charms turn pale.
- Tap **End Chain** to complete the move (needs at least 2 charms): the chain
  pops off the board and its points bank. Longer chains are worth far more
  (400 for 2 … 8,600 for 13!).
- The 💎 **switcher** (corner diamonds) joins any chain and lets it change
  styles. **Bonus +2,000** for ending a chain on the switcher, and another
  **+2,000** for chaining *all* charms of one style in a single chain.
- From round 2, **blocker** pieces appear — they can't be chained and your
  tube must route around them.
- The ball tray is your **timer**. Clear the board to advance a round and win
  time back; hit 250,000 for the bonus round. Out of balls = game over.
  **Take Score** banks your total and ends the game on your terms.

High score (with your initials, arcade style) and longest-link records are
saved locally.

## 📱 Playing on iPhone

1. Open `index.html` in Safari (host it anywhere static — e.g. enable GitHub
   Pages on this branch — or just save the file to the Files app and open it).
2. Optional: **Share → Add to Home Screen** to install it full-screen like a
   native app. Landscape matches the original arcade layout; portrait works
   too.

## 🛠 Tech notes

- Vanilla JS + one `<canvas>`: procedurally drawn clover-grass frame, dirt
  board, cross dividers, and glossy vector charms (no image assets).
- Chain reachability is a turn-limited BFS (≤2 bends) through empty cells;
  blockers and already-chained pieces block paths.
- Scoring curve reverse-engineered from real gameplay footage:
  per-piece 200, 200, 200, 400, 400, 600, 600, … (+2,000 bonuses).
- Web Audio synthesized sound effects (iOS-safe unlock on first tap).
- Smoke-tested headlessly with Playwright: chain/score math, invalid-link
  rejection, switcher style-reset, round flow, timeout, and layout in both
  orientations.
