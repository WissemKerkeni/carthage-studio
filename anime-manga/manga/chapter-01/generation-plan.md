# Chapter 1 — Generation Plan

**Status:** `PROPOSED`. **Nothing here has been generated.** No image-generation integration is
connected to this project — see `README.md` §Tooling status. This file is the plan that runs the
moment one is.

**Standing rule:** approval is required before each stage. A stage does not begin until the
previous stage's assets are approved, because every later generation carries the earlier ones as
references. Generating out of order is how a project ends up with 200 chapters that do not match.

---

## Stage 0 — Style anchors

**4 images. Must be approved before anything else is generated, including character sheets.**

| ID | Subject | Why first |
|---|---|---|
| STY-01 | A rope walk in hard noon light: three tone densities, three line weights, heavy solid blacks | Becomes the style reference attached to **every subsequent generation in the series** |
| STY-02 | Face standard — adult male, three-quarter, restrained expression | Fixes eye design, nose treatment, expression ceiling |
| STY-03 | Architecture standard — Phoenician harbour, ruled perspective | Fixes how buildings are drawn for 200 chapters |
| STY-04 | Crowd standard — individuals in front, silhouette behind | Fixes crowd handling, needed for pp. 7–11 |

**Gate:** the author approves STY-01 before STY-02–04 are attempted. If STY-01 is wrong, everything
after it is wrong, and cheaply fixing it here saves regenerating hundreds of panels later.

## Stage 1 — Character references

**Only characters appearing in chapter 1.** Full sheets per `characters/README.md`.

| ID | Character | Sheets | Notes |
|---|---|---|---|
| CHR-12 | Elishat, 14 | Front, side, back, face, expressions, **hands**, + poses | The hands sheet is not optional — see `CHR-12` do-not-drift §2 |
| CHR-34 | Yatonbaal | Front, side, **back (working posture, walking backwards)**, face, hands | The back sheet matters more than usual: much of scene 2 is shot from behind |
| CHR-33 | Zakarbaal | Front, side, face, **hands (soft)**, temple-formal variant | His hands sheet and Elishat's are the chapter's thesis and should be reviewed side by side |
| CHR-06 | Sosylos | **Hands and desk only. No face sheet.** | Face is withheld until ch. 124; do not generate one, so it cannot leak into a panel by accident |

**Age variants not needed for this chapter.** Elishat's 20 and 55 sheets are required before
ch. 15 and ch. 21 and can wait.

**Gate:** all four approved, and Elishat's and Zakarbaal's hands sheets approved *together*, before
any location work.

## Stage 2 — Location references

| ID | Sheet | Used on pages |
|---|---|---|
| LOC-01a | Tyre — the island from the sea, low angle | 5–6 |
| LOC-01b | **The rope walk, one-point, south to north** | 13, 33, 39 |
| LOC-01c | The rope walk — working detail: posts, tar pot, top cart, hemp yard | 14–21, 39 |
| LOC-01d | The murex shore and shell mounds | 8 |
| LOC-01e | The Sidonian harbour front and counting houses | 10–11 |
| LOC-01f | Sosylos' room — desk, window, wall | 1–4 |

**LOC-01b is the chapter's most-reused asset** and should be approved with the most care.

## Stage 3 — Panels

126 panels across 42 pages. Generated **page by page, in page order**, on explicit request
("Generate page 13"), never as a batch.

Per page: panel specs written from `_TEMPLATE-panel.md` → prompts derived from the approved
character, location and style references → generation → QC against the 13-point checklist →
approve or regenerate **only the failing panels**.

### Recommended first page

**Page 13** — the full-page establishing shot of the rope walk.

Not page 1. Page 13 is the single hardest image in the chapter (four-hundred-pace one-point
perspective, ruled architecture, hemp dust, figures at depth, the diagonal shadow that must be
continuity-correct). If the pipeline can produce page 13 to standard, it can produce this chapter.
If it cannot, that is worth knowing before 41 other pages have been made.

### Matched pairs — generate together, never separately

| Pair | Pages | Why |
|---|---|---|
| The hemp yard | 14 and 39 | Same angle, same framing; the difference between them is the chapter's only plot evidence |
| The hands | 35 (both panels) | Zakarbaal's and Elishat's, compared in one beat |
| The lane | 13 and 42 | The opening and closing images of the set |

## Cost and volume

| Stage | Assets | Est. generations at 3 attempts each |
|---|---|---|
| 0 — style | 4 | ~12–20 (anchors usually take more) |
| 1 — characters | ~22 sheets | ~66 |
| 2 — locations | 6 | ~18 |
| 3 — panels | 126 | ~378 |
| **Total** | **~158 assets** | **~470–500 generations** |

Panels will exceed three attempts each in practice; consistency work on faces and hands is where
the real volume goes. **Treat ~500 as a floor, not an estimate.**

## Unknowns — partly resolved 2026-09-20

> **See `visual/generation-tooling.md`** for verified findings. Headline: Midjourney has **no API**,
> and **Niji 7 has no character-reference parameter** — `--cref` is V6/Niji 6, `--oref` is V7, the
> Edit Model is V8.x. Point 3 below is therefore confirmed as the project's central risk, and the
> proposed answer is a Midjourney-for-design / ComfyUI-for-production split.

## Unknowns to resolve when an integration is connected

1. **Which generator, and which model version.** The prompt-constraint block in
   `visual/manga-style.md` is written but untested; its phrasing will need tuning to whatever is
   actually connected.
2. **Supported parameters must be verified at that time, not assumed.** Do not carry over
   parameters from documentation or memory of an earlier version.
3. **Character-reference support** — whether the connected tool can carry a character reference
   across generations determines whether 200 chapters of consistency is achievable at all, or
   whether the project needs a different approach (a trained model, or human artists working from
   these sheets).
4. **Whether panels are generated individually and composited, or pages generated whole.** This
   plan assumes individual panels composited into pages, which is the only approach compatible with
   the "regenerate only the problematic panel" rule.

**Point 3 is the real risk in this project**, and it is worth testing with the Stage 1 sheets
before committing to Stage 3.
