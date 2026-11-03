# Changelog

All notable changes to Render queues. Newest first.

## 1.1.0 · 3 Nov 2026
*Release order*

- Each app card shows its release order, read from a `## Release order` list in the app's `RENDER_QUEUE.md`: numbered, with each item's reason and **Ready** or **Waits for Q##**, then an Any time list, and a "Not in the order" line for blocked, building and not-yet-approved items.
- An Order check appears only when the list is wrong: an item above something it needs, an approved item missing, a shipped item still listed, an unknown ID, or a line it can't read.
- **Up next** at the top: each app's next build with Copy build. Tap a row to jump to it.
- Next build now takes the first Ready item in the release order (it used to take the first Approved row, which showed Q31 and Q18). Apps without a list work as before.
- Mac and wide screens: the release order sits beside the app name, under Next build.

## 1.0.0 · 3 Nov 2026
*First version*

- Reads each app's `RENDER_QUEUE.md` and `CHANGELOG.md` live from GitHub on open, on Refresh and when the page comes back on screen, with a "Checked" time.
- Needs you strip: awaiting your Render, and approved, awaiting Build, per app, plus a Building line. "All clear" when there's nothing.
- iPhone: swipeable app cards with an app switcher and page dots, opening on the app that needs you most. Mac: three rows with the queue and changelog side by side.
- Each card: last shipped, Next build, the queue in groups with Copy render and Copy build, a collapsed Shipped list sorted by version, the latest 5 versions with their notes, and an "Out of step" note when the queue and changelog disagree.
- Dots for anything new since your last visit, and Mark all seen.
