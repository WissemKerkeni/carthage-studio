# Generation Tooling — findings and recommendation

**Status:** `PROPOSED`. Verified against Midjourney's official documentation on **2026-09-20**.
Supersedes the assumptions in `manga/chapter-01/generation-plan.md` §Unknowns.

> **Standing rule from `README.md`:** do not assume a Midjourney parameter is available. This file
> records what was verified and when. **Re-verify before locking any prompt text** — this landscape
> moved three times in the eighteen months before this check.

---

## 1. Verified facts — Midjourney, as of 2026-09-20

| Fact | Detail |
|---|---|
| Current default version | **V8.2**, released 24 July 2026 |
| Current anime model | **Niji 7**, launched 9 January 2026. **There is no Niji 8** |
| Niji 7 character handling | Docs: *"follows prompts more closely, which helps with specific designs or repeatable characters"*; *"more literal"*; *"a cleaner, flatter look designed to highlight its improved line work"* |
| Character Reference `--cref` | **V6 and Niji 6 only.** Not supported on anything newer |
| Omni Reference `--oref` / `--ow` | **V7 only.** `--ow` 1–1000, default 100, keep under 400. Costs **2× GPU time**. Incompatible with Fast Mode, Draft Mode, Conversational Mode and `--q 4` |
| Edit Model | **V8.x only.** Replaces Omni Reference, Character Reference and Retexture. Supports **up to four reference images** |
| Style Reference `--sref` | Supported across V6, V7 and V8.x |
| API | **None. Midjourney has never shipped a public API.** Discord bot and web app only |

## 2. The problem this creates

**Every character-reference mechanism is version-locked, and none of them covers Niji 7.**

```
--cref  ──→ V6 / Niji 6          (old model)
--oref  ──→ V7                   (not the anime model)
Edit Model ─→ V8.x               (not the anime model)
Niji 7  ──→ no character reference at all
```

So the best anime model Midjourney has is the one model with no way to say *"this specific person
again."* For a series with **46 named characters recurring across 200 chapters, with age variants
spanning 55 years**, that is not a detail. It is the central production risk, and it is the same
risk already flagged as point 3 of the generation plan's unknowns.

## 3. Three ways to stay inside Midjourney

| Option | Gets you | Costs you |
|---|---|---|
| **Niji 6 + `--cref`** | An actual character-reference parameter | An older model: worse coherency, worse hands, worse fine detail — and `style-guide.md` §3 makes hands a signature of this series |
| **Niji 7, prompt + `--sref` only** | The best line work available, and the flat clean look the style bible already describes | No character lock. Consistency rests on the canonical description, the frozen prompt block and QC rejection |
| **V8.2 + Edit Model** | The strongest reference tooling MJ has — four reference images | Not the anime model. Manga look must be driven entirely by prompt and `--sref` |

**None of them is automatable**, because there is no API.

## 4. What actually solves 200-chapter consistency

Reference parameters produce *a similar character*. They do not produce *the same character*, and
across 200 chapters the drift compounds. The two techniques that do work in production:

1. **Train the character into the model — a LoRA per main character**, from the approved reference
   sheets. The character stops being a prompt and becomes part of the weights. This is what the
   character files in `characters/` were built to be training data for.
2. **ControlNet for composition** — enforce camera angle, figure placement and framing from a
   sketch or pose input. **This turns `storyboard.md` and `page-plan.md` from documentation into
   actual pipeline inputs**, which is worth a great deal given how much of this project is
   composition specification.

Neither is possible in Midjourney. Both are standard in ComfyUI.

## 5. Recommendation — a hybrid, `PROPOSED`

**Do not abandon Midjourney. Use it for the thing it is genuinely best in the world at, then hand off.**

### Phase 1 — Midjourney / Niji 7, for design

Stage 0 (4 style anchors) and Stage 1 (~19 character sheets). About **23 images, done manually**,
no API, no ToS exposure. Midjourney's art direction and aesthetic quality are the reason to use it,
and Niji 7's flat, clean, strong-line-work look is close to what `style-guide.md` §1–2 already
specifies. This phase *finds and locks the look.*

### Phase 2 — ComfyUI, for production

Once the sheets are approved, they become **LoRA training data**. Panel production moves local:

- **MCP-connectable** — community ComfyUI MCP servers exist; a specific one gets verified and wired when we reach this point. This is the "supports MCP" the author asked for.
- **Reproducible** — seeds plus saved workflow graphs mean a panel can be regenerated exactly. That is the `v001/v002` discipline this project already requires, enforced by the tool instead of by hand.
- **Free per image** after hardware.
- **Consistent**, because the character is in the weights.
- **Composition-controllable** via ControlNet, driven by the storyboards.

**Cost:** a capable GPU (owned or rented), and a real technical setup. Not trivial.

### Why the handoff does not lose the look

The LoRAs are trained on the *approved Midjourney sheets*. The house style carries across because
the training data is the house style. This is the standard route for AI-assisted comics at length.

## 6. If local infrastructure is not wanted

A middle path: a hosted model with a real API and multi-image reference support — Flux via
fal.ai or Replicate, or Google's Gemini image models. Automatable and MCP-reachable, far less setup
than ComfyUI, meaningfully less control, and no LoRA training. Better than manual; weaker than
Phase 2.

## 7. Decisions this file does not make

1. **Which Midjourney model for Phase 1** — Niji 7 (best look, no character lock) or V8.2 + Edit Model (best reference tooling, not the anime model). **Author's call.** Affects the `manga-style.md` prompt block.
2. Whether Phase 2 happens at all, or the project stays manual throughout.
3. Whether this becomes a human-artist bible instead — still a legitimate outcome, and the `characters/` and `locations/` files serve that use unchanged.

**Nothing in `manga-style.md`'s prompt-constraint block is frozen until decision 1 is made.**

## Sources

- [Midjourney — Version](https://docs.midjourney.com/hc/en-us/articles/32199405667853-Version)
- [Midjourney — Omni Reference](https://docs.midjourney.com/hc/en-us/articles/36285124473997-Omni-Reference)
