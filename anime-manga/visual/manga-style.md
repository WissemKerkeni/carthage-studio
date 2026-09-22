# Manga Style — Production Rules

**Status:** `PROPOSED`. Inherits everything in `style-guide.md`; this file holds only the
print and black-and-white specifics.

## Format

| Decision | Value | Status |
|---|---|---|
| Page dimensions | 2150 × 3035 px at 600 dpi (B5 tankobon trim, 182 × 257 mm) | `PROPOSED` |
| Safe area | 15 mm from trim on all sides; nothing load-bearing outside it | `PROPOSED` |
| Bleed | 3 mm, used only on the panels listed in `style-guide.md` §9 | `PROPOSED` |
| Colour | Pure black and white with screentone. No greyscale painting | `PROPOSED` |
| Spreads | Reserved. Book One has exactly two: the sacks going over the rail (ch. 4), and the pyre (ch. 18) | `PROPOSED` |

## Panel composition rules

| Rule | Value | Status |
|---|---|---|
| Default eyeline | Standing adult eye height. The camera is a person, not a drone. Low and high angles are statements and are used sparingly | `PROPOSED` |
| Establishing cadence | Every scene opens on an establishing shot, and re-establishes after any panel that changes the reader's sense of where people are | `PROPOSED` |
| Max consecutive same-size panels | Three. A fourth is a deliberate choice meaning monotony, labour, or waiting | `PROPOSED` |
| Page-turn policy | Every reveal lands on the first panel after a turn — that is, on an **even** page in right-to-left binding. Nothing is revealed at the bottom of an odd page | `PROPOSED` |
| 180-degree rule | Enforced within a scene. A deliberate break marks a betrayal or a reversal, and is logged in the page plan | `PROPOSED` |
| Silence | At least one wordless panel per page, and at least one fully wordless page per chapter | `PROPOSED` |

## Readability checklist — applied per page

- [ ] Reading order unambiguous right-to-left without effort
- [ ] Balloons do not cross panel borders or cover faces
- [ ] Speaker identifiable for every balloon
- [ ] Figure separates from background by tonal value
- [ ] No two adjacent panels at identical scale and angle
- [ ] The beat of the page lands on the largest panel
- [ ] Page reads at 60% reduction (phone screen test)

## Prompting rules — learned in Phase 0, 2026-09-20

These are not style opinions. They are observed behaviour of `gemini-3-pro-image`, and every
character, location and panel prompt in this project follows them.

### 1. Describe what is there. Never list what is not.

**Negative prompts barely work.** `"No Greek or Roman columns"` was in a prompt verbatim and the
model returned fluted columns and a triangular pediment. It only changed when the building was
described positively — flat roof, blank windowless walls, recessed doorway, two freestanding pillars.

The same applied to faces: `"he is not handsome"` produced a handsome man. `"A broad flattened
nose, a heavy asymmetric brow, one eye set slightly lower than the other, deep creases at the
mouth"` produced the approved STY-02.

**Consequence for this project:** every `do-not-drift` list must be rewritten into positive
description before it enters a prompt. The list stays as it is for QC; the prompt gets the
affirmative form.

### 2. Keep prompts short, or the style slips.

Lengthening a prompt to nail one detail caused the model to trade away rendering discipline.
The over-specified hand attempt returned **six digits and a smooth grey wash instead of
screentone** — failing the two most basic criteria — while the shorter prompt had produced correct
anatomy and crisp halftone.

**Consequence:** state the subject plainly, attach the style block, and **fix remaining detail by
editing rather than by adding sentences.**

### 3. Edit; do not regenerate.

`inputImagePath` edits preserve composition, tone and line style while changing one named element.
This is how STY-01 was finished: the best composition was kept and only the temple was replaced,
after three full regenerations each lost something the previous one had.

**Consequence:** a panel that is 90% right is never thrown away. It is edited. This is also what
makes "regenerate only the failing panels" achievable at all.

### 4. The camera drifts. State it explicitly.

Asked repeatedly for a strict centred one-point perspective, the model drifted to raised,
three-quarter and diagonal views, losing the composition each time a different element was fixed.
Camera position, eye height and vanishing-point placement have to be stated as instructions —
*"camera at standing eye level, on the ground in the middle of the lane, looking straight down its
length, vanishing point at the centre of the frame"* — and verified on every establishing shot.

### 5. "Lighter" and "softer" are not the same instruction.

Asked for a lighter, higher-key page, a **face** held its register — because the prompt carried hard
plainness anchors (*broad flattened nose, heavy brow, deep creases, receding hairline*). A **crowd**
given the same lightening instruction, but no plainness anchors, collapsed into children's-book
illustration: round faces, large eyes, smiling children.

**Consequence:** the light page treatment is safe and is now canon. The words *softer* and *rounder*
are banned from prompts. **Every prompt containing people carries at least one plainness anchor.**

### 6. State the age as a number, in every prompt, including chained ones.

**Age is the axis that drifts, and it drifts older.** Chaining a close-up from an approved
full-body reference held identity perfectly — the same face, hair, cord tie and expression — but
aged a fourteen-year-old to roughly eighteen. **Editing afterwards barely moved it.** Restating the
age numerically in a fresh chained generation, with child-specific anchors (short rounded face,
soft jaw, fuller cheeks, head large relative to shoulders), worked where the edit did not.

Close-ups drift older than full-body shots — there is more room for adult facial structure.

**Consequence:** every prompt states the character's age in that chapter as a number, and
**apparent age is a QC check in its own right.** This matters more in this series than in most:
Hannibal ages 9 to 64 on screen and Elishat 14 to 55.

### 7. Surface features edit well. Structure does not.

A pattern across every edit attempted so far:

| Edits reliably | Resists editing |
|---|---|
| Hair length and style | **Apparent age** |
| An object — a building, a pillar, a statue | **Body proportion and build** |
| Background content | |
| Sky and atmosphere | |
| Line weight and tonal key | |

Replacing a Greek temple, cutting hair to the jaw, removing statues from pillars and rendering a
sky all worked in a single pass with everything else preserved. Instructing "make her look
fourteen" and "make him short and slight with thin legs" both produced only partial movement, and
in the second case silently dropped an established detail (tar staining to the elbows).

**Also resistant: small localised detail.** Instructing that four fingernails on one named hand be
blackened to match the other produced a visually unchanged image. So it is not simply "structure
resists" — it is that the edit needs a **large, clearly bounded subject**. A temple, a head of
hair, a sky and a pair of statues all edit cleanly; four fingernails do not.

**Consequence:** age, height, build and proportion are **baked into the first generation**, never
corrected afterwards. When they come out wrong, regenerate with the attribute stated numerically
and anchored — do not try to edit toward it.

Asked repeatedly for a strict centred one-point perspective, the model drifted to raised,
three-quarter and diagonal views. Camera position, eye height and vanishing-point placement must
be stated as instructions, and even then are verified on every establishing shot.

### 9. "Japanese" in the style block can drift the SETTING to Japan.

**The worst failure in the project so far.** A wide shot generated *without* a chained character
reference came back with the standing figure in a **kimono**, the labourer in a **conical straw
hat**, and a **pagoda-roofed temple** at the end of the lane — while the prompt explicitly said
*"an ancient Phoenician city, 9th century BC"* and *"a small flat-roofed temple"*.

The two panels beside it on the same page, chained from character sheets, were flawless.

The style block says *Japanese seinen manga*. Without an image anchor and with a loosely named
garment — *"a plain well-made full-length robe"* — the model applied Japanese **setting**, not just
the Japanese **drawing idiom**. Naming the period did not save it; rule 1 again — a negative or a
bare label loses to a concrete description.

**Consequences, all three required:**

1. **Every panel containing people is chained from a character reference.** No exceptions.
2. **Garments are named specifically** — *"ankle-length Levantine tunic-robe with straight vertical folds and a plain round neck"*, not *"a robe"*; *"short undyed linen kilt to the knee"*, not *"a kilt"*.
3. **Write "Japanese seinen manga drawing style"**, and place the setting anchor next to each figure rather than only at the end of the prompt.

In a two-character panel the one-reference limit means the second figure will drift. Chain the more
distinctive character, then **edit the other's hair and beard in** — surface features, which rule 7
says take cleanly. That worked here.

### 8. The generator cannot produce B5. Compose for the crop.

`manga-style.md` sets the page at **B5, 1.41:1**. The generator offers 3:4 (1.33) and 2:3 (1.50) —
**neither is the page** — and a full-page panel's frame is narrower still: with 15 mm insets the
panel is 1442 x 2327, an aspect of 1.61.

Page 13's art lost **610 px of width, 17%**, in assembly. An even crop clipped the foreground
worker's hands at the panel edge, against the series' own hands principle. Taking the whole cut
from the left preserved him, and the wall still carried the diagonal.

**Consequence:** full-page panels are composed knowing they will be cropped. Load-bearing content —
figures, hands, the vanishing point — goes **centre and right**; the left carries expendable mass
such as a shadow field or a wall. The crop is then chosen at assembly rather than defaulting to centre.

---

## Generation-time constraints

Standing text appended to every manga panel prompt. Composed once the style is approved;
it is the mechanism that keeps 200 chapters looking like one series.

```
Japanese seinen manga artwork, black and white. Fine brush-inked linework with
natural taper; the contour heavier than the interior line but not dominating it.
Shading done almost entirely with adhesive screentone at three densities with
visible halftone dot texture; hatching used sparingly. The sky is rendered in
screentone — textured cloud and haze, lighter toward the horizon — never left as
blank paper. Solid black fills for hair, dark cloth, doorways and deep shadow,
with generous clean white paper in the lit areas. Simplified manga facial
construction: the nose suggested with a short line and a small shadow, the mouth
a simple line, eyes almond-shaped and restrained with a single small highlight.
Plain, unglamorous, weathered faces. Strong figure-to-ground separation,
background in finer lighter line. Architecture in ruled straight lines and strict
perspective. Realistic adult proportions, roughly seven and a half heads tall,
unheroic. Ancient Near Eastern Phoenician setting, 9th century BC. No panel
border, no frame. No colour.
```

**Status:** `CANON`, register revision 2026-09-20. Revised from the block that produced STY-01/02
v001: finer line, rendered skies, and an explicit plainness anchor.
It is attached to every generation, together with the approved anchor images as style references.

Model and settings are recorded in `assets/ASSET-LOG.md`. **Re-verify supported parameters before
any future model change rather than assuming them.**
