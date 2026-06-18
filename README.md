# kaef.life — priority by position

An Eisenhower-style task matrix you run in **sprints**. Tap to drop a task; position = priority (horizontal: less urgent → urgent, vertical: less important → important). Private, on-device; each install gets a random 5-digit id.

## The matrix
Fills the screen as an **adaptive rectangle** (portrait or landscape) with a frame, using all available space. Positions are stored as fractions, so they hold at any aspect ratio.

## Sprints & task identity
- The **current sprint is the only editable one.** Tasks there are single live entities — editing, moving, completing, or deleting acts on the one object.
- **Past sprints are frozen, read-only history.** When you start a new sprint, the current one closes: a snapshot of every task is kept as a record (done = strikethrough, unfinished = "carried"). In a closed sprint you can look but not touch.
- **Incomplete tasks move forward keeping the same identity** (same id), with importance and urgency each reduced by 10 points. **Completed tasks stay behind** as a frozen record and don't carry over.
- **List view is the full history**: every sprint as its own section (newest first), each task/record with a delete button — so you can prune entries even in closed sprints. Done shows struck through, slipped tasks show "carried".
- An **empty, closed sprint can be deleted** (from the matrix or its List section); remaining sprints renumber 1, 2, 3…

## Navigating / starting a sprint
- Forward — swipe left, press `→`, or tap `›`. From the latest sprint this opens a **confirmation** showing exactly what carries over vs. what freezes; confirm to start.
- Back — swipe right, press `←`, or tap `‹` to review frozen sprints.

## Files
`index.html` (the whole app), `manifest.webmanifest`, `service-worker.js`, `icons/`, `bichradio-light.css`.

## Deploy (Vercel)
Push to your production branch. When you ship updates, bump the cache name in `service-worker.js` (currently `kaef-shell-v4`) so returning visitors don't load a stale shell.

## Storage & migration
`localStorage` behind a small `Store` interface (in-memory fallback if blocked). Old saves auto-migrate: a single board becomes Sprint 1; any prior multi-sprint data freezes earlier sprints into history and keeps the latest open. The storage key never changes, so existing users keep their data.

## Postponed
Cross-device sync and shareable links — they slot into the `Store` layer later without an app rewrite.
