# Changelog

All notable changes to Render queues. Newest first.

## 1.0.0 · 3 Nov 2026
*First version*

- Reads each app's `RENDER_QUEUE.md` and `CHANGELOG.md` live from GitHub on open, on Refresh and when the page comes back on screen, with a "Checked" time.
- Needs you strip: awaiting your Render, and approved, awaiting Build, per app, plus a Building line. "All clear" when there's nothing.
- iPhone: swipeable app cards with an app switcher and page dots, opening on the app that needs you most. Mac: three rows with the queue and changelog side by side.
- Each card: last shipped, Next build, the queue in groups with Copy render and Copy build, a collapsed Shipped list sorted by version, the latest 5 versions with their notes, and an "Out of step" note when the queue and changelog disagree.
- Dots for anything new since your last visit, and Mark all seen.
