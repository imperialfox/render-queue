# Render queues

![version](https://img.shields.io/badge/version-1.1.0-blue)

**Current version:** 1.1.0 · see the [changelog](CHANGELOG.md).

One page that shows, at a glance, what's waiting for a **Render** (approval) and what's approved and waiting for a **Build**, across three apps: Vocal Sessions, Suki and ivanc.digital.

## Where the data comes from

Nothing is copied in by hand. Every time the page opens, when Refresh is tapped, and when it comes back on screen, it reads each app's `RENDER_QUEUE.md` and `CHANGELOG.md` straight from GitHub (`main` branch):

| App | Repo |
|---|---|
| Vocal Sessions | `imperialfox/Vocal-Sessions` |
| Suki | `imperialfox/Suki` |
| ivanc.digital | `imperialfox/ivanc.digital` (no render queue yet; it's picked up automatically once `RENDER_QUEUE.md` appears) |

It reads the raw files first. If they can't be reached and the page is running inside Claude, it tries a GitHub connector instead. If one file fails, only that spot shows "Couldn't load … Retry".

- **Queues:** the markdown table and the `## Release order` list are read; the other prose is ignored. Vocal Sessions' "Earlier working names" column is hidden.
- **Changelogs:** Vocal Sessions and Suki versions start `## 3.50 · 3 Nov 2026` with an italic headline underneath. ivanc.digital versions start `## 0.2.31 - 2026-10-24`; the first bullet, shortened, is the headline. Versions are compared number by number (2.10 is newer than 2.9).

## The release order

Each app's `RENDER_QUEUE.md` keeps the order to build in, as a short list. Names come from the queue table, so each line only needs the ID and a reason; "needs Q##" in the reason (one or more IDs) is what the page reads.

```
## Release order
1. Q40 — touches the whole stylesheet, so first
2. Q37 — brings the pitch listener
3. Q38 — needs Q37

### Any time
- Q31 — tooling, no app version
- Q35 — needs Q31
```

- **Ready:** Approved, and everything it needs has shipped. Otherwise it shows **Waits for Q##**, or its own status if it isn't approved yet.
- **Next build** and **Up next** take the first Ready item (the numbered list first, then Any time). An app with no list works as before: the first Approved row.
- **Order check** (only when something's wrong): an item above something it needs, an Approved item missing from the list, a shipped item still listed, an ID that isn't in the table, or a line the page can't read.
- Render places an item in the list and the Build that ships it removes it; each app's queue says so at the top.

## What's on the page

- **Top bar:** Checked time, Refresh, Mark all seen.
- **Up next:** each app's next build (the first Ready item in its release order), with Copy build. Tapping a row goes to that app and highlights it.
- **Needs you:** awaiting your Render, and approved, awaiting Build, with a per-app breakdown. Tapping a tile goes to that app and highlights those items; tapping again moves on to the next app that has some. A small line shows anything Building.
- **App cards:** last shipped, Next build (with Copy build), the release order (numbered, then Any time, a "Not in the order" line, and an Order check only when needed), the render queue in groups (Building, Approved, Awaiting Render, Blocked), a collapsed Shipped list sorted by version, the latest 5 changelog versions (tap to read the notes, Show all for the rest), and an "Out of step" note only when the queue and changelog disagree.
- **Copy buttons** copy e.g. `Vocal Sessions Q07 Render` or `Suki Q18 Build`.
- **New since last visit:** a dot on new changelog versions and on queue items whose status changed. Remembered on this device only. Mark all seen clears them.

### Layouts

- **iPhone:** swipe between the three app cards (or use the app buttons or page dots). Opens on the app that needs you most.
- **Mac and wide screens:** three rows, each with the queue on the left and the changelog on the right.

## Add it to the Home Screen

1. Open the page in Safari.
2. Tap Share, then **Add to Home Screen**.
3. Tap **Add**.

On a Mac, in Safari choose File › Add to Dock.

## Changing the icon

Replace `icon.png` (180 × 180), bump `?v=1` on the `apple-touch-icon` link in `index.html`, then remove the Home Screen icon and add it again (iOS only reads the icon when it's added).

## Adapting it

The apps are listed once near the top of the script in `index.html` (`APPS`): name, short name, button label and repo. Add a line to add an app.

## Data and privacy

The page only reads public files from GitHub. The only thing it saves is what it saw last time (for the "new" dots), in this browser's storage on this device.

## Stack

One `index.html`: plain HTML, CSS and JavaScript, no frameworks, no build step. Hosted on GitHub Pages.

## Licence

MIT. See [LICENSE.txt](LICENSE.txt).
