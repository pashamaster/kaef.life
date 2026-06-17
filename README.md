# Matrix — priority by position

An Eisenhower-style task matrix. Tap the canvas to drop a task; its **position is its priority** — horizontal = urgency, vertical = importance. Everything lives on the device. No account, no PII; each install gets a random 5-digit id (a label for now, an identity hook for sync later).

## Files
- `index.html` — the whole app (CSS + logic inline). Self-contained app shell.
- `manifest.webmanifest` — install metadata.
- `service-worker.js` — offline app-shell cache.
- `icons/` — app icons (192, 512, maskable, svg).
- `bichradio-light.css` — the design system converted to the bright theme, as a standalone file for future screens.

## Run it
**Quick look:** open `index.html` directly in a browser. The matrix, dragging, and labels all work. (Service worker and "Add to Home Screen" need real hosting; see below.)

**As an installable PWA** — serve the folder over `localhost` or HTTPS:
```bash
cd matrix
python3 -m http.server 8000
# visit http://localhost:8000  → browser menu → Install / Add to Home Screen
```

## Storage
Data persists in `localStorage` behind a small `Store` interface in `index.html`. If storage is blocked (e.g. a sandboxed preview frame), the app falls back to in-memory and says so in the hint line, so the demo still works for the session.

## Next: option 4 (sync)
The app never touches storage directly — only `Store.load()` / `Store.save(state)`. To add passkey login + encrypted cross-device sync later, swap those two methods' internals for IndexedDB + WebCrypto + a sync call. No app logic changes.
