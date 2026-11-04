# Handoff

The dashboard belongs to no app, so its work has no queue ID. Each version gets its own **Render** (scope approved) and **Build** (go-ahead), recorded here, newest first.

## Ideas (not scheduled)

Kept here so they aren't lost. None is planned or approved; each needs a Blueprint and its own Render.

- **Kit builds on the page (4 Nov 2026).** Kits (`imperialfox/parts-kit`, `atlas-kit`, `prototype-kit`) have no `RENDER_QUEUE.md`, so a kit version that must come before an app item never shows in Up next or Next build. Example: parts kit 1.1 had to ship before Vocal Sessions' Q41, but Up next showed Q38. One way: also read each kit's `HANDOFF.md` (its Render and Build stamps) and show approved kit versions, with "needs" lines in an app's Release order able to name them. Ivan: "add that as an idea so it doesnt get lost."

## Next version · Size ring, order rows and hold to copy

**Render:** 4 Nov 2026, 19:24. Ivan: "render", for the Blueprint (Ivan's project note `render_queues_size_chip_blueprint.md`, parts 1 to 3) with every *Default if unanswered*, as one Build.
**Build:** awaiting. The version is settled when it lands (Build receipts and *1.2 · Run together* are also waiting).

**Goal:** see each build's size at a glance, read the Release order faster, and copy a Build line with one press and hold.

**Agreed**
1. **Size ring:** a five-segment ring under the status pill, no text. Light 1 green, Light to medium 2 yellow-green, Medium 3 amber, Medium to heavy 4 orange, Heavy 5 red; filled segments take the step's colour, the rest faint grey. 16 px. Screen readers and Mac hover give the size word.
2. **Where the ring shows:** Release order rows; Approved, Awaiting Render and Building queue rows; the Next build box.
3. **Source:** a new `Size` column in Vocal Sessions' and Suki's `RENDER_QUEUE.md` tables (full step). Blank or unreadable means no ring, never a warning. Starting values: Vocal Sessions Q42 Heavy, Q43 Medium, Q44 Light to medium, Q45 Medium; Suki Q20 Medium, Q21 Light.
4. **Release order rows:** ID chip and title; a **Requires** line (only when something is named): shipped items as a blue chip with a tick and "- shipped 3.55", others plain grey; the description (the reason without its "needs" part and date stamp), two lines, tap for the rest; a plain outlined chip "Ivan, DD/MM/YY" from the line's stamp. On the right, **Ready** or **Waiting**, with the ring under it.
5. **Suki's Release order lines** (Q20, Q21) get the "(Ivan, 1 Nov 2026)" stamp. A line with no stamp shows no date chip.
6. **Press and hold** (0.5 s) a row to copy its line, as the Copy buttons do (`Vocal Sessions Q42 Build`; Awaiting Render rows copy the Render line), with the toast `Copied "Vocal Sessions Q42 Build"`. The row dims while held; on the iPhone the copy happens on lift; text selection and the callout are off on these rows; a short tap still opens the description. Works on Release order rows, Approved and Awaiting Render rows, Next build and Up next. Copy buttons stay.
7. Each app's Render rule gains "fill the Size column and stamp the Release order line". Documentation-only commits in the app repos, no app versions.
8. Named parts `size-ring`, `order-requires`, `order-desc`, `order-approved`, `hold-copy`; no new saved data. Screenshot checks as 1.1, plus a headless press and hold.

**Out of scope:** the Up next strip's layout, shipped rows, guess vs real from receipts, reading kit versions (so "Parts kit 1.2" stays grey), ivanc.digital, any queue item's status or scope, app code, haptics.

**Done when:** the real Release orders show Q42 "Requires Q41 - shipped 3.55", Q45 with two grey chips and Q20 "Requires Q19 - shipped 2.25"; rings match the starting values; holding Q42 copies "Vocal Sessions Q42 Build" with the toast on the iPhone; blank Size or no stamp shows nothing extra; dark mode reads well; nothing else changes; live on Pages.

**Effort guess:** Medium.

## Next version · Build receipts

**Render:** 3 Nov 2026, 18:38. Ivan: "Go ahead with both of them, render", for part B of the Blueprint (Ivan's project note `build_receipts_blueprint.md`) with every *Default if unanswered*. Part A (his `ivan-app-style` skill) has its own Build outside this repo.
**Build:** awaiting. The version is settled when it lands: 1.2.0 if it ships before *1.2 · Run together* (Blueprint, not yet rendered), otherwise 1.3.0.

**Goal:** every queue Build leaves a receipt of what it cost, and each app card shows them, so guesses at Render can be checked against what builds really took.

**Agreed**
1. A `BUILD_RECEIPTS.md` in each app's repo (and in kit repos for kit builds): a table, newest first: Date · Item · Version · Guess · Real · Steps · Written · Re-read · Full test runs · Biggest share.
2. No past builds counted. The first row is Vocal Sessions Q40 (measured in its build); the rest start with the next Build.
3. The page reads it live, like `CHANGELOG.md`; a missing file means "no receipts yet", never a warning.
4. Each app card gets a Receipts part, collapsed like Shipped: the latest receipt drawn in the receipt style, earlier ones one line each, and a tally (on the money · went over · came in under).
5. Starting files: Vocal Sessions with Q40's row; Suki empty with its header. Documentation-only commits, no app versions.
6. Named parts `receipts`, `receipt-latest`, `receipt-row`, `receipt-tally`; no new saved data; screenshot checks as 1.1.

**Out of scope:** counting past builds, cost in money, charts over time, any queue item's status or scope, app code and versions.

**Done when:** Vocal Sessions' card shows Q40's receipt and a tally of 1 on the money; Suki shows "No receipts yet"; nothing else changes; live on Pages.

## 1.1.0 · Release order

**Render:** 3 Nov 2026, 13:30. Ivan: "Render", for the Blueprint (Ivan's project note `render_queues_1_1_release_order_blueprint.md`) exactly as written, with all ten defaults, as one Build in the order below.
**Build:** 3 Nov 2026, 13:36. Ivan: "Build". Shipped as **1.1.0**.

**Goal:** show the order to release approved builds, per app and as an Up next strip, and warn when the order breaks a "needs".

**Agreed**
1. This file holds the dashboard's own records.
2. Each app's `RENDER_QUEUE.md` keeps a `## Release order` list (`N. Q## — reason`, then `### Any time` with `- Q## — reason`); "needs Q##" in the reason is what the page reads; names come from the table.
3. Ready = Approved and everything it needs has shipped; otherwise "Waits for Q##", or the item's own status if it isn't approved.
4. Next build = the first Ready item (numbered list, then Any time). No list → the first Approved row, as in 1.0.0.
5. Order check, only when wrong: above something it needs; an Approved item missing; a shipped item still listed; an ID not in the table; a line that can't be read.
6. "Not in the order" line for Building, Blocked and Awaiting Render items that aren't listed.
7. Up next strip under Needs you: one row per app with Copy build; tapping a row goes to that app and highlights it.
8. Wide screens: the release order sits under Next build in the card's top row.
9. No test suite; screenshot checks instead.
10. Starting order: Suki Q22, Q23, Q18, Q19, Q20, Q21. Vocal Sessions Q40, Q37, Q38, Q39; any time Q31, Q35.

**Out of scope:** ivanc.digital (no queue yet), any queue item's status or scope, app code and versions, working the order out automatically, "new" dots for order changes, a test suite, screen IDs.

**Done when:** Up next shows Suki Q22 and Vocal Sessions Q40; both cards show their order with Ready/Waits as above; no Order check on the real queues; it appears with a broken copy; with no list a card works as 1.0.0; 1.1.0 is live.

### Debrief

- **Built in order:** Vocal Sessions `RENDER_QUEUE.md` list and rule, plus the same step in `.agents/skills/render-approval/SKILL.md` (`f3cd311`); Suki `RENDER_QUEUE.md` list and rule (`fde48bb`); this repo's `index.html`, `README.md`, `CHANGELOG.md` and this file.
- **Decided within scope:** the list reader also takes `1)` numbering and bold IDs; a line that starts like a list item but has no readable ID is reported in the Order check, never guessed. Retired items count as done for "needs". The Release order chips are tappable, like the rest, to show the item in the queue groups.
- **Named parts:** `up-next`, `up-next-row`, `release-order`, `order-row`, `order-check`, `not-in-order`. No new saved data.
- **Checks:** `node --check`; headless screenshots from local copies of the queues at 390 and 375 wide (light and dark) and Mac 1440×900, with the real queues, Vocal Sessions without a list (Next build fell back to Q31, as 1.0.0), a broken Suki copy (all four warnings shown) and ivanc with no queue. No sideways scroll; the only console error is the expected 404 for ivanc's missing queue (same as 1.0.0). Tapping a Suki Up next row moved to the Suki card.
- **Note:** the page shows no version number, so on the phone 1.1.0 shows as the Up next strip appearing.
