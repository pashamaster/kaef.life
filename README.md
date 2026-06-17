# kaef.life — priority by position

An Eisenhower-style task matrix. Tap the canvas to drop a task; its **position is its priority** — horizontal = urgency, vertical = importance. Mark a task done and it **stays on the board, struck through**, so the picture of what you've cleared stays intact. Everything lives on the device; each install gets a random 5-digit id.

The matrix **scales to the full screen width** — it sizes itself to the largest square that fits between the header and the dock.

## Files
- `index.html` — the whole app (CSS + logic inline).
- `manifest.webmanifest`, `service-worker.js`, `icons/` — PWA scaffolding.
- `bichradio-light.css` — the design system, bright theme, standalone for future screens.

## Run it
**Quick look:** open `index.html` in a browser — matrix, dragging, labels all work.

**As an installable PWA** — serve over `localhost` or HTTPS:
```bash
python3 -m http.server 8000   # visit http://localhost:8000 -> Install / Add to Home Screen
```

## Storage
Data persists in `localStorage` behind a small `Store` interface. If storage is blocked (e.g. a sandboxed preview frame) it falls back to in-memory and says so in the hint line.

## Postponed
Cross-device sync and shareable links are deferred. The app only ever calls `Store.load()` / `Store.save(state)`, so adding passkey login + encrypted sync later is a change to the storage internals, not a rewrite.
