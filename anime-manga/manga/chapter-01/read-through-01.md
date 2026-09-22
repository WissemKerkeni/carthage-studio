# Chapter 1 — read-through 01

**Date:** 2026-09-22 · **Reviewer:** Claude (director) · **Build:** all pages v001
**Method:** reviewed as **openings**, not as single pages — the flow a reader actually sees.

> **Pagination used.** Right-to-left binding. Within an opening the reader takes the **right** page
> first. Openings are therefore `(3|2)`, `(5|4)`, `(7|6)` … with p. 1 and p. 42 alone.
> This matches `page-plan.md`'s own binding note: *"the reader turns from an odd page to an even one."*

---

## DEFECT 1 — the Tyre spread is broken by pagination `BLOCKING`

**`page-plan.md` specifies the spread at pages 5–6. Those two pages are never seen together.**

| Opening | Left | Right |
|---|---|---|
| 3 | **p. 5 — right half of the spread** | p. 4 — Sosylos' hands |
| 4 | p. 7 — the streets | **p. 6 — left half of the spread** |

Each half of the series' signature Tyre image sits in a different opening, facing an unrelated page.
The scale reveal — the whole point of spending a spread — does not happen.

**This is an error in the page plan, not only in the build.** A spread must occupy one opening,
so the only valid slots are **{2,3}, {4,5}, {6,7}, {8,9}…** — an even page and the odd page above it.
`5–6` is `{odd, even}` and cannot work under any binding convention, because the pairing is the
same whether p. 1 is recto or verso.

**Options:**

1. **Move the spread to 6–7.** Page 5 becomes a single page and page 7's five street panels are
   redistributed. Costs one new page of content. **Recommended** — it keeps the frame (pp. 1–4) intact.
2. **Move the spread to 4–5.** Cheaper, but p. 4 is the frame's *"hard cut out"* full page —
   the last image before Tyre — and folding it into the spread loses the cut.
3. Add a page to the frame so everything shifts by one. Changes the chapter to 43 pages.

**Blocked:** the `mcp-image` server failed to connect this session, so the new art cannot be
generated yet.

## DEFECT 2 — page 41 carries unauthorised sound effects `BLOCKING`

The bottom panel of p. 41 has **hand-drawn katakana SFX written into the artwork** — ギュッ and ザッ.
The generator added them; they were not placed at assembly.

This breaks three rules at once:

- `script.md` scene 4: *"No dialogue. No narration. No sound effect."*
- `style-guide.md` §10: SFX are **low volume** and this series has very few of them
- The stray-text failure mode already logged on p. 32 (*"LAYING CART"*)

The marks are, annoyingly, well drawn and apt — ギュッ is a tightening sound. They still have to go.

**Second instance of the same failure mode.** Two in one chapter means it is systematic, not a
one-off, and **every panel must be scanned for stray text before assembly.** Adding to
`manga-style.md` as a standing QC item.

**Blocked** on the same server failure.

## DEFECT 3 — page 13 is marked a reveal but sits on a left page `MINOR`

`page-plan.md` marks p. 13 *"Location reveal"*, and its own rule states that **every reveal must
land on the first panel of an even page.** Page 13 is odd, so it is read *second* in its opening;
p. 12 takes the after-the-turn position.

In practice it survives — p. 13 is a full page and dominates the opening regardless — but the plan
contradicts itself. Either re-label p. 13 as a beat, or accept that full-page images are exempt
from the rule and say so.

**The two reveals that matter are correct:** p. 24 (the second shadow) and p. 38 (*"nothing at all"*)
both land on even pages, in the after-the-turn position, exactly as planned.

---

## What works

- **pp. 36–37 share an opening** — the question and the reply are read together, then the reveal waits for the turn to p. 38. That is the scene's best structural decision and it survives into the built pages.
- **pp. 34 → 35 across the gutter.** Her eyes lift and find his hands on the right page; the thesis lands on the left. The eyeline crosses the gutter and pulls the reader into it.
- **p. 33 reads as intended even at thumbnail size.** The two wides are near-identical and the shadow difference is visible — the "nothing has happened but time" device survives reduction.
- **pp. 12 → 13.** The dark gap between buildings on the right, the sunlit lane on the left. The reader comes out of the dark into the lane within one opening.
- **p. 38's exit.** Three narrowing verticals read right to left, the figure shrinking. Clearest sequence in the chapter.

## Pacing note — the heavy stretch

Pages **14, 15, 16, 20, 21** are all process pages of similar tonal weight, and in the contact sheet
the run 13–21 reads as one long grey block. This *is* the design — `chapter.md` spends twelve pages
on the work deliberately — but it is the place a test reader is most likely to stall, and it comes
**before** the pp. 30–33 gamble rather than after it.

No change recommended yet. **Flag it for the first outside reader** and see whether they slow down
there or at 30–33. The answer decides which sequence gets cut if the chapter has to lose pages.

---

## Verdict

**Two blocking defects, one minor, both blockers waiting on the image server.**

Nothing found in character continuity, location continuity, reading order, balloon placement or
the do-not-drift lists. The failures are a **pagination error inherited from the page plan** and a
**generator artifact** — neither is a failure of the art or the references.
