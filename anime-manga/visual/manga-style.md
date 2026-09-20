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

## Generation-time constraints

Standing text appended to every manga panel prompt. Composed once the style is approved;
it is the mechanism that keeps 200 chapters looking like one series.

```
black and white manga panel, screentone shading at three densities only,
three line weights, hard high-left key light, ruled architectural perspective,
realistic 7.5-head anatomy, restrained facial expression, detailed hands,
heavy solid blacks, no colour, no chibi, no speed lines, no sparkle,
no abstract background, no modern objects
```

**Status:** `PROPOSED` — not final until STY-01 is approved and the phrasing is tested against the
actual generator, whose supported parameters must be verified at that time rather than assumed.
