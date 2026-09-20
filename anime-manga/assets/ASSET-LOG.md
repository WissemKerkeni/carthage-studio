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

## Panel assets

None generated yet.
