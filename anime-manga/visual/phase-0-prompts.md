# Phase 0 — Look Development Prompt Set

**Status:** `PROPOSED`, ready to run. Derived from `style-guide.md` and `manga-style.md`.
Target: **18 prompts × 2–3 variations = 36–54 images.** Output lands in `assets/_staging/`.

**Purpose:** find the house style, and produce the 4–8 images that become `visual/references/`
STY-01 to STY-04 — which then attach as style references to **every generation in the series**.

**This is M0, the go/no-go.** If the manga look will not come out of this model, we learn it here.

---

## Prompting note — this is Gemini, not Midjourney

Gemini responds to **descriptive natural language**, not comma-separated tag soup and not
`--parameters`. Every prompt below is written as prose instruction. Danbooru-tag style would be
right for an Illustrious-family model and is wrong here.

**Prompt enhancement is disabled** (`SKIP_PROMPT_ENHANCEMENT=true`) so these reach the model
verbatim. That is deliberate — see the commit on `.mcp.json`.

---

## The constant block

Appended to every prompt in this set. It is the style bible compressed to what a model can act on.

```
Black and white manga artwork. No colour anywhere. Traditional screentone shading at
three densities only — light, medium, dark — with visible halftone dot texture, not smooth
grey gradients. Three line weights only: heavy contour, medium interior, fine texture.
Architecture and ships drawn with ruled straight lines and strict perspective; flesh, rope,
cloth and rock drawn freehand. Hard high sunlight from the left, deep solid black shadows,
blown-out white highlights, very little midtone. Realistic adult proportions, roughly seven
and a half heads tall, unheroic bodies. Restrained facial expressions. Small almond eyes with
a single small highlight. Hands drawn in full detail. Ancient Mediterranean, 9th century BC,
Phoenician. No modern objects. No Greek or Roman columns. No colour, no glow, no sparkle,
no lens flare, no digital painting, no soft airbrush rendering.
```

---

## Group A — The master anchor (STY-01)

**The most important images in the set.** STY-01 becomes the style reference for the entire series.

| ID | Tests | Prompt (+ constant block) |
|---|---|---|
| **A1** | The chapter 1 hero angle; ruled one-point perspective; figures at depth | *A long narrow open sand lane running straight away from the viewer, four hundred paces, seen in one-point perspective. Low stone wall on the left. Wooden spinning posts in rows. Six workers in undyed linen walking backwards away from the camera, ropes around their waists, paying out hemp yarn as they go. Hemp dust hanging in the shafts of light. A temple's shadow falls diagonally across the lane. Midday, hard sun.* |
| **A2** | Same, tighter; texture of the trade | *Close view of rope-making: a worker's hands twisting three strands of hemp yarn into cable, fibres visible, tar staining the fingers. Sand floor. Hard sunlight, deep shadow.* |
| **A3** | Can it hold flat B&W under a complex subject? | *A rope walk at midday seen from a low angle, the temple of a Phoenician city rising behind it, workers small against the architecture.* |

## Group B — Face standard (STY-02)

**The restraint test.** The single biggest risk is that the model returns pretty, rendered,
wide-eyed anime. The style bible's expression ceiling is low and its eyes are small.

| ID | Tests | Prompt |
|---|---|---|
| **B1** | Male face, restraint, eye design | *Portrait of a weathered Phoenician man of about forty, three-quarter view, cropped black hair and short untended beard, deeply sun-damaged skin, narrow eyes permanently squinting from years of working in glare. His expression is neutral and closed. He is not handsome.* |
| **B2** | Female face, plainness, no beauty pass | *Portrait of a fourteen-year-old Levantine girl, three-quarter view, black hair cut at the jaw and tied back with cord, broad flat cheekbones, thin mouth, heavy-lidded steady dark eyes. Plain-featured, tired, watchful. Working clothes.* |
| **B3** | Grief without distortion (`style-guide.md` §4) | *Close portrait of a woman of about thirty receiving bad news. Her face does not move. She is not crying. Temple clothing, dark hair pinned up.* |
| **B4** | Elite grooming vocabulary | *Portrait of a Phoenician priest of about forty-five, soft indoor complexion, black hair going iron-grey, oiled and arranged in tight formal curls, full square beard oiled and curled to match. Tired, heavy-lidded, faintly worried.* |

## Group C — Architecture standard (STY-03)

| ID | Tests | Prompt |
|---|---|---|
| **C1** | The signature Tyre image; ruled perspective at scale | *An ancient Phoenician island city seen from the sea at low angle: a dense wall of leaning mudbrick and cedar buildings five and six storeys high, crowded to the waterline, two tall bronze pillars rising above them on the high ground. Packed harbour in front. Hard midday sun.* |
| **C2** | Interior, black-dominant (`§6`: fear is drawn as black) | *A cramped lamp-lit Phoenician counting room, ledgers and clay tablets on a low table, deep shadow filling most of the frame, one small high window.* |
| **C3** | Ship construction, researched not generic | *A Phoenician merchant sailing ship of the 9th century BC drawn up on a shallow shore: single mast, square sail furled, high curved stern, steering oars, open hold. Workers unloading. Hard sun.* |
| **C4** | Industrial texture, ugliness | *A shoreline of ancient purple-dye works: rows of stone vats, mounds of crushed murex shells taller than a man, flies, workers with stained arms. Unglamorous and filthy.* |

## Group D — Crowd standard (STY-04)

| ID | Tests | Prompt |
|---|---|---|
| **D1** | Individuals in front, silhouette behind (`§7`) | *A crowded ancient harbour quayside, packed with dockworkers, porters and traders. The nearest two rows of people are drawn as distinct individuals with detailed faces; everyone behind them is rendered in flat silhouette.* |
| **D2** | Crowd density as a plot fact | *A narrow street between six-storey mudbrick buildings, so crowded there is no sunlight at ground level, laundry strung overhead, people shouting from upper floors.* |

## Group E — Hands

**This series' signature** (`style-guide.md` §3). Four distinct pairs must be visually separable,
and generative models are historically weakest here. **Test it early and hard.**

| ID | Tests | Prompt |
|---|---|---|
| **E1** | Rope hands — the chapter's thesis, half one | *Extreme close-up of a young girl's small working hands splicing rope: heavy callus across the base of every finger and along the outer edge of the palm, tar permanently black in the nail beds and knuckle creases. Strong, broad, disproportionate to her size.* |
| **E2** | Soft hands — thesis, half two | *Extreme close-up of a middle-aged priest's soft, unmarked, uncallused hands holding the hem of an expensive robe clear of tar on the ground. One old burn scar across the left palm. An indentation on the right middle finger from writing.* |
| **E3** | Old hands, the frame | *Extreme close-up of an elderly man's hands resting on a wooden desk beside a weighted papyrus scroll. Dust in the light. The face is not visible.* |

## Group F — Atmosphere and dust

`style-guide.md` §8: **dust is this series' weather.**

| ID | Tests | Prompt |
|---|---|---|
| **F1** | Heat as blown-out white | *An empty sunlit sand lane at noon, almost entirely white, with one small figure and a hard black shadow. Heat haze. Minimal detail.* |
| **F2** | Emptiness and negative space | *A bare hill above an empty bay and a shallow lagoon at the end of the day, North African coast, nothing built on it. Wide, empty, quiet.* |

---

## Review criteria — how each image is judged

Objective, so review is not taste. An image **fails** if any of these is true:

| # | Failure |
|---|---|
| 1 | Any colour at all |
| 2 | Smooth grey gradients instead of halftone screentone dots |
| 3 | More than three tonal densities; muddy midtones everywhere |
| 4 | Soft digital painting or airbrush rendering instead of line art |
| 5 | Large anime eyes, multiple highlights, sparkle, or glow |
| 6 | Exaggerated expression beyond the §4 ceiling |
| 7 | Banded gloss highlight in hair |
| 8 | Malformed hands in any image where hands are the subject |
| 9 | Perspective that is not ruled or not consistent |
| 10 | Classical Greek/Roman columns, pediments, or white marble |
| 11 | Any modern object |
| 12 | Glamour lighting, beauty framing, or a subject made attractive against the brief |

**Pass = the image could sit on the same page as the other passes and look like one artist.**

## What comes out of this

| Outcome | Then |
|---|---|
| Most pass | Pick the best 4–8 → `visual/references/` as STY-01 to STY-04. **M0 passes.** Proceed to character sheets |
| Line art fails but composition is good | Retry with a stronger constant block; if it still fails, the model cannot do B&W manga |
| Screentone consistently fails | **Switch to Seedream** (`ARK_API_KEY`, same server) before spending more |
| Hands consistently fail | Serious. Re-plan: hands may need a human pass, and `style-guide.md` §3 may need revising |

## Cost

36–54 images at `IMAGE_QUALITY=quality`. Verify current Gemini image pricing at run time;
this is the cheapest stage in the project and the one with the highest leverage.
