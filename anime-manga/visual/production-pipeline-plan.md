# Production Pipeline Plan — one tool, no training

**Status:** `PROPOSED`, revised 2026-09-20 to the author's constraints.
Verified tooling facts: `visual/generation-tooling.md`.

**Author's constraints, all binding:**
one tool · no model training · no local setup · manga/anime quality · MCP support.

**All five are satisfiable.** This plan does that.

---

## The decision

| Layer | Choice |
|---|---|
| **Tool** | **Nano Banana Pro** (Google's Gemini image model) |
| **Connection** | **One MCP server.** Mature options exist; the specific one is verified and wired at setup |
| **Consistency** | **Reference images, up to 14 per generation.** No training, ever |
| **Setup** | An API key. Nothing installed on this machine |

One service. One MCP server. One model. No LoRAs, no ComfyUI, no GPU, no Midjourney.

## Why this, and why the constraint is now reasonable

When this project was planned, "no training" meant accepting serious character drift. **That is no
longer true.** The 2026 benchmarks are explicit: reference-based approaches now perform close to
trained models for most production work, and LoRA is only clearly better for characters with highly
unusual features. The technology moved to meet the constraint.

Nano Banana Pro specifically:

| Capability | Why it matters here |
|---|---|
| **Up to 14 reference images per generation** | Character sheet + location sheet + style anchors, all passed on **every single panel**. This is the consistency mechanism |
| **Character consistency is its headline strength** | The exact pain point in a 200-chapter series |
| **Conversational editing** | Fix one thing in a panel in plain language, keeping the character. Replaces "regenerate and hope" |
| **Up to 4K output** | `manga-style.md` specifies 2150 × 3035 px at 600 dpi. Reachable |
| **Real API + multiple MCP servers** | I generate, read the image back, QC it against the character file, and log it — inside this session |

## The honest trade

**Nano Banana is not an anime specialist.** Niji is more aesthetically refined for anime out of the
box, and I am not going to pretend otherwise.

What closes the gap: the **14 reference slots**. Once the style anchors are approved, they ride
along on every generation as style references. That is how the house style gets enforced without
training — and it is stricter than a prompt, because it is an image.

**If Phase 0 shows the manga look will not land**, the same class of MCP server also supports
**Seedream 5.0**, whose "Universal Reference" system is built for exactly this. Swapping is a
config change, not a new pipeline. Recorded as the fallback, not the plan.

---

## The consistency mechanism — we already built it

This is the part worth understanding. In a no-training pipeline, consistency comes from four things,
and **three of them are already written**:

| Mechanism | Where it lives | Status |
|---|---|---|
| Reference images passed per generation | `assets/characters/`, `assets/locations/`, `visual/references/` | Produced in Phases 0–2 |
| Canonical description + frozen prompt block | Every `CHR-*` and `LOC-*` file | **Written** |
| Do-not-drift list per character | Every `CHR-*` file | **Written** |
| QC rejection against the 13-point checklist | `_TEMPLATE-panel.md`, `manga-style.md` | **Written** |

The character bible is not documentation in this pipeline. **It is the pipeline.** Every hour spent
on `CHR-12`'s hands or `CHR-33`'s soft palms pays out directly, because those lines become prompt
text and those sheets become reference images.

**The one honest cost of no-training:** drift is higher than with LoRA, so more generations get
rejected. We absorb that by rejecting them — `README.md`'s rule already says continuity outranks
image quality.

---

# PHASE 0 — Look development

1. Author creates an API key (see *Setup*, below).
2. I wire the MCP server and **verify what the model actually supports at that moment** — reference-image count, resolution, aspect ratios — rather than trusting documentation.
3. I write exploration prompts from `style-guide.md`: three line weights, three tone densities, hard high-left key light, restrained expression, heavy solid blacks, *weight · heat · restraint*.
4. **I generate directly over MCP** — 30–60 explorations: rope walks, harbours, faces, hands, crowds, interiors.
5. I read every image back and review against the style bible. We cut to the **4–8 that define the series**.
6. Those become `visual/references/` STY-01 to STY-04 — **and they are attached as style references to every generation thereafter.**

**Gate:** author approves the look. **Go/no-go on the whole approach** — if the manga style will not
come out of this model, we learn it here for a few dollars, and switch to Seedream.

# PHASE 1 — Character references

Chapter 1 cast only:

| # | ID | Character | Note |
|---|---|---|---|
| 1 | CHR-12 | Elishat | Hands sheet mandatory — `style-guide.md` §3 |
| 2 | CHR-34 | Yatonbaal | Back / working posture; much of scene 2 is shot from behind |
| 3 | CHR-33 | Zakarbaal | Soft hands — the chapter's visual thesis |
| 4 | CHR-06 | Sosylos | **Hands and desk only. No face** — withheld until ch. 124 |

Per character: generate from the canonical description + style anchors → curate the sheet set
(front, side, back, face, expressions, hands) → **validate against the do-not-drift list in three
unseen situations** → approve → `assets/characters/`, logged in `ASSET-LOG.md`.

**Gate:** Elishat's and Zakarbaal's hands sheets reviewed **side by side**.

# PHASE 2 — Location references

LOC-01 Tyre (six angles), LOC-16 the ships, LOC-18 the bay and hill.
**LOC-01b — the rope walk, one-point, south to north — is the most reused asset in the chapter.**

# PHASE 3 — Panels

1. **Page by page, in page order.** Never batched.
2. Every generation carries: style anchors + the character sheets of everyone in frame + the location sheet. That is the 14 reference slots doing their job.
3. **Page 13 first** — the hardest image in the chapter. If page 13 works, chapter 1 works.
4. QC against the 13-point checklist. Fix single panels with **conversational editing** rather than regenerating from scratch.
5. **Compositing and lettering stay human** — Clip Studio Paint, Krita or Affinity. No generator letters manga.

---

# Setup — what the author does

1. **Get a Google AI Studio API key** for the Gemini image model.
2. **Tell me**, and I will give exact instructions for where the key goes in the MCP configuration.
3. That is all. Nothing is installed on this machine.

> **Credential handling.** The author places the key into the MCP config. **Do not paste an API key
> into chat.** I will never ask for the key itself.

# Cost

Per-image pricing, no subscription. **Verify current rates at Phase 0** — they move, and 4K costs
more than standard resolution.

| Phase | Images |
|---|---|
| 0 — look development | 30–60 |
| 1 — character sheets | ~25 |
| 2 — location sheets | ~10 |
| 3 — chapter 1 panels | 126, plus rejections |

# Milestones

| # | Milestone | Gate |
|---|---|---|
| M0 | MCP connected; style anchors approved | **Go/no-go — does the manga look land?** |
| M1 | Four character sheets pass do-not-drift validation | Author approves |
| M2 | Location sheets approved | Author approves |
| M3 | Page 13 generated to standard | Author approves |
| M4 | Chapter 1 complete, 42 pages | Author approves |

**Nothing past M0 is worth committing to until M0 passes.**

## Sources

- [mcp-image — one server, Nano Banana / GPT Image / Seedream](https://github.com/shinpr/mcp-image)
- [Nano Banana MCP Server](https://mcpservers.org/servers/nanana-app/mcp-server-nano-banana)
- [Consistent characters with AI, 2026](https://getimg.ai/blog/how-to-create-consistent-characters-with-ai)
- [2026 AI image API benchmark](https://www.atlascloud.ai/blog/tips/2026-ai-image-api-benchmark-gpt-image-2-vs-nano-banana-2-pro-vs-seedream-5-0)
