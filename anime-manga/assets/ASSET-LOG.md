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
| CHR-12-hands | Elishat's hands — rope callus, tar-black nail beds | `assets/characters/CHR-12-elishat-hands-v001.jpg` | v001 | 2026-09-20 | **approved** |

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

## Location and panel assets

None generated yet.
