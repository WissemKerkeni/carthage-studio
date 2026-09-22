# Asset Log

Every generated asset is recorded here before it is used as a reference for anything else.
An approved asset is never overwritten — a change produces the next version.

**Status values:** `generated` → `review` → `approved` / `rejected` / `superseded`

**Approved** means: it passed QC, it is canon, and later generations must match it.

**Staging images are not committed** (see `.gitignore`). This log is the record of what was
generated, what it cost and why it passed or failed. Approved assets are committed.

---

## Standing generation settings

| Setting | Value |
|---|---|
| Tool | `mcp-image` v0.14.0 (MCP) |
| Model | `gemini-3-pro-image` |
| Provider | gemini |
| Quality | `quality` |
| Prompt enhancement | **disabled** — canon-derived prompts must reach the model verbatim |
| Output | `assets/_staging/`, promoted on approval |

---

## APPROVED — style anchors

| Asset ID | Subject | File | Ver | Date | Derived from | Status |
|---|---|---|---|---|---|---|
| **STY-01** | Master style anchor — the rope walk, one-point perspective | `visual/references/STY-01-rope-walk-v002.jpg` | **v002** | 2026-09-20 | v001, edited: rendered sky + finer line | **approved** |
| STY-01 | — earlier register, blank sky | `visual/references/STY-01-rope-walk-v001.jpg` | v001 | 2026-09-20 | `A1-v002` + `v005` temple edit | **superseded** |
| **STY-02** | Face standard — plain adult male, three-quarter, restrained | `visual/references/STY-02-face-standard-v002.jpg` | **v002** | 2026-09-20 | staging `B1-v003-plain` re-run in the lighter register | **approved** |
| STY-02 | — earlier register, heavier tone | `visual/references/STY-02-face-standard-v001.jpg` | v001 | 2026-09-20 | staging `B1-v003-plain` | **superseded** |
| **STY-03** | Architecture standard — Tyre from the sea | `visual/references/STY-03-architecture-v001.jpg` | v001 | 2026-09-20 | first pass, edited to replace Roman honorific columns with plain pillars | **approved** |
| STY-04 | Crowd standard | — | — | 2026-09-20 | — | **rejected** |
| **STY-05** | **Weight standard** — rendered sky as subject, tiny figure, sombre | `visual/references/STY-05-weight-v001.jpg` | v001 | 2026-09-20 | first pass | **approved** |

**The register was revised partway toward a lighter page** after the author supplied two reference
pages: finer line, more white paper in lit areas, and **rendered skies**. STY-05 was added because
nothing in the bible anchored *weight* — every previous anchor was hard noon sun.

**STY-01, 02, 03 and 05 are attached as style references to every subsequent generation.**

## APPROVED — character references

| Asset ID | Subject | File | Ver | Date | Status |
|---|---|---|---|---|---|
| CHR-12-front | Elishat, front, full body, age 14 | `assets/characters/CHR-12-elishat-front-v001.jpg` | v001 | 2026-09-20 | **approved** |
| CHR-12-side | Elishat, left profile, full body | `assets/characters/CHR-12-elishat-side-v001.jpg` | v001 | 2026-09-20 | **approved** |
| CHR-12-face-3q | Elishat, three-quarter head study | `assets/characters/CHR-12-elishat-face-3q-v001.jpg` | v001 | 2026-09-20 | **approved**, age residual |
| CHR-12-hands | Elishat's hands — rope callus, tar-black nail beds | `assets/characters/CHR-12-elishat-hands-v001.jpg` | v001 | 2026-09-20 | **approved** |
| CHR-34-front | Yatonbaal, front, full body, age 38 | `assets/characters/CHR-34-yatonbaal-front-v001.jpg` | v001 | 2026-09-20 | **approved**, build residual |
| CHR-33-front | Zakarbaal, front, full body, age 45 | `assets/characters/CHR-33-zakarbaal-front-v001.jpg` | v001 | 2026-09-20 | **approved** |
| CHR-33-hands | Zakarbaal's hand — soft, uncallused, censer scar | `assets/characters/CHR-33-zakarbaal-hands-v001.jpg` | v001 | 2026-09-20 | **approved** |
| CHR-06-hands-desk | Sosylos' hands, desk and scroll. **No face** | `assets/characters/CHR-06-sosylos-hands-desk-v001.jpg` | v001 | 2026-09-20 | **approved** |

**Chapter 1's cast is now referenced.** The gate in `chapter-01/generation-plan.md` — Elishat's and
Zakarbaal's hands reviewed side by side — is **passed**: hers is dense with callus, tar-black nail
beds and heavy tone; his is pale, smooth, unmarked but for the censer scar, and carried almost
entirely in white paper. The chapter's visual thesis reads without a caption.

**Yatonbaal's build residual.** His first pass came out as an athletic figure with a defined torso,
against a canon description of *lean, heavy forearms and shoulders, thin legs*. An edit flattened
the torso and thinned the legs but only partially, and **silently dropped the tar staining to the
elbows** established in the first pass. Accepted as a neutral model sheet — the tar is scene
dress and is carried in his wardrobe notes — but his proportions should be re-checked in panels,
and a side and back sheet generated with the build stated up front rather than edited toward.

### CHR-12 — the consistency test, and what it showed

The front view was generated from the canonical description with no image reference: **the tuned
text block alone held the register.** Its first pass gave her shoulder-length hair with a braid,
violating do-not-drift §5 (jaw-length, never flowing); one edit fixed the hair and cleared the
background while preserving face, pose and clothing.

The side and face views were then **chained from the approved front** via `inputImagePath`.

**Identity held.** Across three generations the same face, the same blunt bob, the same plain tired
expression, and even the small cord tie at the nape were retained without being re-described.
This is the mechanism the whole no-training approach depends on, and it works.

**Age did not hold.** The chained close-up aged her from fourteen to roughly eighteen. An edit
instructing "make her look fourteen" barely moved it. A fresh chained generation that **stated the
age as a number** with child-specific anchors got closest, and is what was approved — still reading
around fifteen or sixteen. Recorded as prompting rule 6.

Generated at short prompt length, then **edited** for child proportions. Anatomy correct, callus
ridges rendered, tar nails correct. **Residual:** scale still reads slightly adult in isolation;
accepted because panels will carry her body in frame to establish scale. The rest of CHR-12's sheet
set is still to be produced.

### STY-01 — provenance

Generated at 3:4, 2K. Composition from the v002 prompt (strict one-point perspective, low wall on
the left only, temple at the vanishing point). v002's temple came out Greek — fluted columns and a
triangular pediment — violating `LOC-01` do-not-drift §5. Rather than regenerate, v002 was **edited**
via `inputImagePath` to replace only the temple with a flat-roofed Phoenician block, blank walls,
recessed doorway and two freestanding pillars. **All other pixels preserved.**

### STY-02 — provenance

Generated at 3:4, 2K. v002 produced the correct manga register but drifted handsome, against
casting rule 1 and `style-guide.md` §12.3. v003 fixed it by **describing plainness positively** —
heavy asymmetric brow, broad flattened nose, thin lips, deep mouth creases, sun-blotched skin —
rather than writing "not handsome".

---

## REJECTED — kept for the record

| ID | Subject | Why rejected |
|---|---|---|
| A1-v001 | Rope walk | European graphic-novel register: cross-hatching carried the shading, uniform pen line. Author chose a Japanese manga idiom instead |
| A1-v002 | Rope walk | Composition correct, but a Greek temple with fluted columns and pediment. **Superseded by the v005 edit, not discarded** |
| A1-v003 | Rope walk | Temple corrected, but lost the one-point perspective — reads as a plaza |
| A1-v004 | Rope walk | Temple correct, composition drifted diagonal again |
| B1-v001 | Face | European graphic-novel register |
| B1-v002 | Face | Register correct, but drifted handsome |
| E1-v001 | Hands | Two interlocking hands, anatomically unreadable; adult, not a child's |
| E1-v002 | Hand | **Anatomy correct, tar nails excellent, crisp screentone.** Still an adult hand; callus not rendered. Best hand so far — the base for the retry |
| E1-v003 | Hand | **Regression: six digits, and grey wash instead of screentone.** Over-specification traded rendering discipline for detail |
| E1-v004 | Hand | Correct anatomy, callus and tar nails all achieved at once, crisp screentone. Still adult in proportion — **the base for the v005 edit** |
| STY-04-v001 | Crowd | **Collapsed into children's-book illustration** — round faces, large eyes, smiling children. Lightening instruction given without plainness anchors. Crowd depth handling was correct and is reusable |

---

## APPROVED — location references

| Asset ID | Subject | File | Ver | Date | Status |
|---|---|---|---|---|---|
| LOC-01a | Tyre from the sea | `visual/references/STY-03-architecture-v001.jpg` | v001 | 2026-09-20 | **approved** — doubles as STY-03 |
| LOC-01b | The rope walk, one-point, south to north | `visual/references/STY-01-rope-walk-v002.jpg` | v002 | 2026-09-20 | **approved** — doubles as STY-01 |
| LOC-01c | Rope walk working detail — tar pot, laying cart, posts, hemp bales | `assets/locations/LOC-01c-ropewalk-detail-v001.jpg` | v001 | 2026-09-21 | **approved** |
| LOC-01d | Murex shore — vats, shell mounds, crushing yards | `assets/locations/LOC-01d-murex-shore-v001.jpg` | v001 | 2026-09-21 | **approved** |
| LOC-01e | Sidonian harbour front — counting houses, tribute ships | `assets/locations/LOC-01e-sidonian-harbour-v001.jpg` | v001 | 2026-09-21 | **approved** |
| LOC-01f | Sosylos' room — desk, window, scrolls | `assets/locations/LOC-01f-sosylos-room-v001.jpg` | v001 | 2026-09-21 | **approved** |

**Stage 2 is complete.** All four generated first-pass with no edits — the first time that has
happened in this project, and a sign the style block and the seven prompting rules have converged.

**LOC-01e is the notable one.** It carries the crowd-depth handling that STY-04 failed at —
individuals in the near rows, flat silhouettes behind — and it worked here because the prompt
carried plainness anchors, exactly as rule 5 predicts. It also stages the chapter's quietest canon
beat without a caption: two foreign officials sitting at their own table with their own tablets,
entirely at ease, and nobody on the quay looking at them.

## APPROVED — pages

| Page | Panels | File | Ver | Date | Status |
|---|---|---|---|---|---|
| **013** | 1 (full page) | `manga/chapter-01/pages/page-013-v001.png` | v001 | 2026-09-21 | **approved** |
| **017** | 4 | `manga/chapter-01/pages/page-017-v001.png` | v001 | 2026-09-21 | **approved**, one residual |
| **035** | 2 | `manga/chapter-01/pages/page-035-v001.png` | v001 | 2026-09-22 | **approved** |
| **036** | 3 | `manga/chapter-01/pages/page-036-v001.png` | v001 | 2026-09-22 | **approved**, placeholder lettering |
| **037** | 3 | `manga/chapter-01/pages/page-037-v001.png` | v001 | 2026-09-22 | **approved**, placeholder lettering |
| **038** | 5 | `manga/chapter-01/pages/page-038-v001.png` | v001 | 2026-09-22 | **approved**, placeholder lettering |
| **001** | 3 | `manga/chapter-01/pages/page-001-v001.png` | v001 | 2026-09-22 | **approved** |
| **002** | 4 | `manga/chapter-01/pages/page-002-v001.png` | v001 | 2026-09-22 | **approved** |
| **003** | 2 | `manga/chapter-01/pages/page-003-v001.png` | v001 | 2026-09-22 | **approved** |
| **004** | 1 | `manga/chapter-01/pages/page-004-v001.png` | v001 | 2026-09-22 | **approved** |
| **039** | 3 | `manga/chapter-01/pages/page-039-v001.png` | v001 | 2026-09-22 | **approved** |
| **040** | 2 | `manga/chapter-01/pages/page-040-v001.png` | v001 | 2026-09-22 | **approved** |
| **041** | 3 | `manga/chapter-01/pages/page-041-v001.png` | v001 | 2026-09-22 | **approved** |
| **042** | 1 | `manga/chapter-01/pages/page-042-v001.png` | v001 | 2026-09-22 | **approved** |

**The first finished page of the series.** 2150 x 3035 px, B5 tankobon at 600 dpi, single bordered
full-page panel inside a 15 mm inset. Spec: `manga/chapter-01/panels/C01-P13-01.md`.

Produced in pipeline order — panel spec written first, then art derived **by edit** from the
approved LOC-01b rather than generated fresh, then assembled to trim. The only generation was one
edit adjusting the shadow to its 120-pace reading and thickening the hemp dust.

**What page 13 proved.** It was chosen as the first page because it is the hardest image in the
chapter. It turned out not to test generation at all — LOC-01b already *was* the image — but to
test **assembly**, and it found a real constraint: the generator has no B5 aspect ratio, so 17% of
the art's width was lost at the panel frame. That is now prompting rule 8, and it changes how every
remaining full-page panel is composed.

### Page 17 — the character-consistency test in composed panels

Four panels, each chained from a different approved CHR-12 sheet: hands for panels 1 and 2, the
face study for panel 3, the front sheet for panel 4.

**Identity held across three scales.** Extreme close-up of hands, close-up of face, wide shot of
the whole figure — recognisably the same person in all of them, with the cord-tied stub at the
nape, the patched shift and the plain tired face carried through without being re-described.
**This is the question the whole no-training approach rested on, and the answer is yes.**

Two failures, both instructive:

- **Panel 1 v001 rejected.** Two hands plus a fid produced three or four overlapping hand masses, anatomically unreadable — the same failure mode as the first E1 attempt. Regenerating with **one hand only** resolved it. Extreme close-ups of two hands doing complex work are this pipeline's weakest case, and the fix is to reduce the number of hands rather than to describe them harder.
- **Panel 2's nail edit did not take.** Instructing that the left hand's pale nails be blackened to match the right produced a visually unchanged image. This refines rule 7: **small localised detail changes resist editing as much as structural ones do.** Replacing a temple or cutting hair works; recolouring four fingernails on one specified hand does not. Accepted as a residual because at 650 px panel width the nails are not legible.

### Page 35 — the thesis

The page the chapter was built around: two pairs of hands, identical framing, identical scale,
identical light. His soft, pale and uncallused; hers with tar-black nail beds on both hands.

**Both pairs were staged at rest**, a refinement on beat 23, which had her splicing while he stood
idle. With neither pair working, the difference is purely what the hands **are** rather than what
they are doing — and they still could not be more different.

Both panels chained cleanly from their approved sheets, first pass, no edits. The tar-nail split
that marred p. 17 panel 02 did not recur.

**Residual left deliberately.** Her hands read closer to adult than fourteen — the same residual
already logged against `CHR-12-elishat-hands-v001`. Not corrected, because the panel matches the
approved sheet and **consistency with the reference outranks being right in isolation.** If it is
ever fixed, the sheet is fixed first and the panels follow.

### Page 36 — two characters in frame, and the first spoken line

The first page carrying dialogue. Pages 1–35 are narration only.

**Two characters held in one frame.** Yatonbaal in the near foreground as a solid black mass,
Zakarbaal standing isolated in the open lane — scale, lighting and register consistent between
them, both chained from their own approved sheets. The 180-degree line set on p. 29 holds.

**Panel 3 was rejected on canon, not on quality.** The crooked left fingers did not read, and
`CHR-34` do-not-drift §3 requires them in every panel showing his hands. Rejected under the
project's own rule that continuity outranks image quality, and regenerated with the deformity as
the subject. **The v002 art should be promoted to CHR-34's hands sheet**, which does not yet exist.

**Lettering is placeholder.** `production-pipeline-plan.md` says lettering stays human; the type
here is Arial set programmatically. It satisfies the balloon-shape vocabulary and proves placement
and reading flow, but it is not final typography.

The first lettering pass was rejected: the balloon overflowed the panel border and clipped its
first line, failing the readability checklist. Placement is now **clamped inside the panel
rectangle and asserted at assembly** rather than trusted to the eye — the assertion caught a 5 px
overflow on the retry, which is exactly what it is for.

### Page 37 — and the worst failure in the project so far

Panels 1 and 2 chained from character sheets and were flawless first pass.

**Panel 3 was generated fresh, without a chained reference, and drifted wholesale into Japan:**
the standing figure in a **kimono**, the labourer in a **conical straw hat**, a **pagoda-roofed
temple** at the end of the lane. The prompt had said "an ancient Phoenician city, 9th century BC"
and "a small flat-roofed temple". Naming the period did not hold it.

The cause is the style block's own words. *Japanese seinen manga*, plus a loosely named garment —
"a plain well-made full-length robe" — and no image anchor, and the model applied Japanese
**setting** rather than Japanese **drawing idiom**. Recorded as prompting rule 9, with three
consequences: chain every panel containing people, name garments specifically, and say "Japanese
seinen manga drawing style".

**v002** chained from Zakarbaal's sheet fixed the setting, but the second figure was not Yatonbaal —
the one-reference-per-call limit biting in a two-character panel. **v003** edited a short untended
beard and greying temples onto him, and they took cleanly, **confirming rule 7 inside a complex
two-figure scene**: chain the distinctive character, edit the other's hair and beard in.

### Page 38 — the reveal, and rule 10

Scene 3 ends. The canon reveal lands on the first panel after the page turn, and the exit is three
narrow verticals read right to left with the figure shrinking across them — near, mid, a mark on
the sand. **The best sequence in the chapter so far**, and all three came back first pass.

**Panels 1 and 2 were rejected on location continuity.** Both were chained from character sheets,
and both invented a setting: a narrow stone alley for one, palm trees and a multi-storey town for
the other, in a scene whose location has been a bare sand lane since page 13. One also drew **its
own internal vertical seam** across the image.

**Cause: the one-reference-per-call limit.** Chaining a character anchors the person, and the
sheets have neutral backgrounds, so nothing anchors the place. Recorded as prompting rule 10 —
in any panel chained to a character, describe the location in the prompt at the same specificity
garments get. Both corrected first pass.

### Pages 1–4 and 39–42 — the chapter's opening and its ending, in one batch

19 panels, 8 pages, one pass. **Pace was the point:** the long per-page specs and per-page commits
of pp. 13–38 existed to capture findings while the pipeline was unproven. With ten rules recorded
and the structural risks retired, that overhead was no longer buying anything, so this batch was
generated in bulk, assembled in one script, spot-checked rather than panel-checked, and committed
once.

**Scene 0** puts Sosylos at the desk with no face, head or shoulders in any panel, and places the
canon narration on the storyboard's exact beats — the hands stop on *"none of them will survive"*,
start again on *"let me begin"*, and the frame closes on *"stolen from a corpse"*.

**Scene 4** is wordless throughout and ends the chapter on page 42: rope filling the frame, no
hands, no people, no words.

**A dependency now runs backwards.** `page-plan.md` makes the hemp yard a matched pair — p. 39's
pile is *"visibly fuller than p. 14"*, and it is the only plot evidence in the chapter. Page 39
exists first, so **p. 14 must now be built to match p. 39's angle and framing** with a smaller pile.

**One layout deviation, flagged not hidden:** p. 1 is three stacked full-width panels rather than
the page plan's *"wide top band, two below"*, because all three images are landscape. Page plan and
art need reconciling.

## Panel assets

15 pages of 42 assembled. 90 panels remain.
