# kaef.life — priority by position

An Eisenhower-style task matrix you run in **sprints**. Tap the canvas to drop a task; its **position is its priority** — horizontal = less urgent → urgent, vertical = less important → important. Mark a task done and it stays on the board, struck through. Everything lives on the device; each install gets a random 5-digit id.

## The matrix
Fills the screen as an **adaptive rectangle** (portrait or landscape) with a small frame, using as much space as the device gives it. Dot positions are stored as fractions, so they hold their meaning at any aspect ratio.

## Sprints
- **Forward** — swipe left, press the right arrow (keyboard `→`), or tap `›`. From the latest sprint this **starts a new one**: every *incomplete* task carries over with importance and urgency each reduced by 10 points (they've aged, so they shift toward less / less). Completed tasks stay behind in the finished sprint as a record.
- **Back** — swipe right, press `←`, or tap `‹` to review earlier sprints.
- New-sprint creation shows an **Undo** for a few seconds.

(Tapping the matrix adds a task; a deliberate horizontal swipe changes sprint — they're separated by movement distance so they don't collide.)

## Files
`index.html` (the whole app), `manifest.webmanifest`, `service-worker.js`, `icons/`, and `bichradio-light.css` (the design system, standalone).

## Run / deploy
Open `index.html` directly for a quick look. For install + offline, serve over HTTPS (you're on Vercel — push to the production branch and it deploys). When you ship an update, bump the cache name in `service-worker.js` (currently `kaef-shell-v2`) so returning visitors don't get a stale cached shell.

## Storage
`localStorage` behind a small `Store` interface; falls back to in-memory if blocked. Old single-board saves auto-migrate to Sprint 1 on first load.

## Postponed
Cross-device sync and shareable links. The app only calls `Store.load()` / `Store.save(state)`, so they slot into the storage layer later without a rewrite.
