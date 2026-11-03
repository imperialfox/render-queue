# Render queues

![version](https://img.shields.io/badge/version-1.0.0-blue)

**Current version:** 1.0.0 · see the [changelog](CHANGELOG.md).

One page that shows, at a glance, what's waiting for a **Render** (approval) and what's approved and waiting for a **Build**, across three apps: Vocal Sessions, Suki and ivanc.digital.

## Where the data comes from

Nothing is copied in by hand. Every time the page opens, when Refresh is tapped, and when it comes back on screen, it reads each app's `RENDER_QUEUE.md` and `CHANGELOG.md` straight from GitHub (`main` branch):

| App | Repo |
|---|---|
| Vocal Sessions | `imperialfox/Vocal-Sessions` |
| Suki | `imperialfox/Suki` |
| ivanc.digital | `imperialfox/ivanc.digital` (no render queue yet; it's picked up automatically once `RENDER_QUEUE.md` appears) |

It reads the raw files first. If they can't be reached and the page is running inside Claude, it tries a GitHub connector instead. If one file fails, only that spot shows "Couldn't load … Retry".

- **Queues:** only the markdown table is read; the prose around it is ignored. Vocal Sessions' "Earlier working names" column is hidden.
- **Changelogs:** Vocal Sessions and Suki versions start `## 3.50 · 3 Nov 2026` with an italic headline underneath. ivanc.digital versions start `## 0.2.31 - 2026-10-24`; the first bullet, shortened, is the headline. Versions are compared number by number (2.10 is newer than 2.9).

## What's on the page

- **Top bar:** Checked time, Refresh, Mark all seen.
- **Needs you:** awaiting your Render, and approved, awaiting Build, with a per-app breakdown. Tapping a tile goes to that app and highlights those items; tapping again moves on to the next app that has some. A small line shows anything Building.
- **App cards:** last shipped, Next build (with Copy build), the render queue in groups (Building, Approved, Awaiting Render, Blocked), a collapsed Shipped list sorted by version, the latest 5 changelog versions (tap to read the notes, Show all for the rest), and an "Out of step" note only when the queue and changelog disagree.
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
