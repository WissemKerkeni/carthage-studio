# CARTHAGE SAGA — Anime / Manga Production Project

**Status: SOURCE STORY DELIVERED — `PROPOSED`, awaiting author approval.**

A historically grounded seinen saga spanning **c. 825–146 BC**: the foundation of Carthage by Tyrian
refugees, its growth into the dominant power of the western Mediterranean, its long wars with the
Greeks and then with Rome, **Hannibal Barca**, and — fifty-six years after his defeat — the
destruction of the city.

**4 seasons · 8 Books · 200 chapters · 100 episodes.** Each season is exactly two Books.

| Season | Books | Chapters | Eps | Ends on |
|---|---|---|---|---|
| 1 | The New City · The Merchant Sea | 1–60 | 26 | Pyrrhus sails; two letters leave Messana |
| 2 | The Sea Between · Truceless | 61–117 | 25 | **The oath at the altar** |
| 3 | Silver · The Road | 118–157 | 24 | **Cannae** |
| 4 | The Long Defeat · The Ashes | 158–200 | 25 | **The fall of Carthage** |

Hannibal is the protagonist and the emotional centre. He is named in ch. 87, first seen at nine in
ch. 115, leads from ch. 134, and dies in ch. 182 — and the sixteen chapters after his death exist to
show what his defeat actually bought, and who it was finally charged to. The treaty he was made to
sign at Zama is the instrument Rome and Masinissa use to strangle the city for fifty-two years.

| Read this first | For |
|---|---|
| [`story/THE-STORY.md`](story/THE-STORY.md) | **The story itself**, 8 Books, c. 825–146 BC (~23,000 words) |
| [`story/historical-dossier.md`](story/historical-dossier.md) | The researched history, every claim tagged by evidence tier |
| [`story/story-bible.md`](story/story-bible.md) | Logline, themes, protagonists, the ten rules, the ending |
| [`story/arcs.md`](story/arcs.md) | All 200 chapters, titled and mapped into 4 seasons |
| [`story/timeline.md`](story/timeline.md) | Both clocks, plus locked character ages |
| [`visual/style-guide.md`](visual/style-guide.md) | The series' visual identity — line, faces, tone, panel language |
| [`manga/chapter-01/`](manga/chapter-01/) | Chapter 1 built out: script, storyboard, 42-page plan, generation plan |

**Evidence discipline.** Every historical claim in this project carries a tier: `[A]` documented ·
`[B]` likely interpretation · `[C]` disputed · `[F]` invented for the story. No invented battle,
treaty, city, king or campaign is ever presented as history; invented *people* may stand beside real
ones but never change a historical outcome. Where the sources disagree, the story picks a reading
and says so — on screen where possible, and always in the appendix to `THE-STORY.md`.

Nothing in this project is `CANON` until the author approves it.

---

## Pipeline

```
STORY -> STORY BIBLE -> WORLD/LORE -> CHARACTER BIBLE -> VISUAL STYLE BIBLE
  -> CHAPTER -> SCENES -> STORYBOARD -> PAGE LAYOUT -> PANELS -> MANGA ART
  -> ANIMATION-READY SHOTS -> ANIME VIDEO
```

The manga is produced first and is the visual source of truth for the anime adaptation.

## Canon status legend

Every claim in every file in this project carries one of these tags:

| Tag | Meaning |
|---|---|
| `CANON` | Established by the author. May not be changed without explicit approval. |
| `PROPOSED` | Suggested by the director (Claude). Not binding until the author approves. |
| `UNCONFIRMED` | Referenced somewhere but never settled. Needs a decision. |
| `RETCON` | A deliberate, approved change to something previously CANON. Records the old value. |

Untagged prose in a template is structure, not story.

## Directory map

| Path | Holds |
|---|---|
| `story/` | Story bible, world, lore, timeline |
| `characters/` | One file per character; canonical descriptions + reference tracking |
| `locations/` | One file per location; same treatment as characters |
| `visual/` | Project visual identity; shared style rules for manga and anime |
| `visual/references/` | Approved style reference images (sref sources, model sheets) |
| `manga/chapter-XX/` | Chapter breakdown, script, storyboard, page plan, page + panel specs |
| `anime/episode-XX/` | Episode script, shot list, animation plan |
| `assets/` | Generated image/video files, plus `ASSET-LOG.md` |

## Conventions

- **Versioning:** assets are `v001`, `v002`, ... An approved asset is never overwritten; a change creates the next version. Approved assets become references for later generations.
- **IDs:** characters `CHR-01`, locations `LOC-01`, panels `C01-P03-04` (chapter 01, page 03, panel 04), shots `E01-S012`.
- **Asset ledger:** every generated asset is recorded in `assets/ASSET-LOG.md` before it is used as a reference.
- **Rejection rule:** a generation that is attractive but violates canon is rejected. Continuity outranks image quality.

## Tooling status

| Capability | Required by workflow | Present in this session |
|---|---|---|
| Project files / Git | yes | available |
| Midjourney / Niji image generation | manga art | **NOT CONNECTED** |
| Higgsfield video generation | anime shots | **NOT CONNECTED** |
| Inline SVG/HTML rendering | page layout mockups | available |

Until an image-generation integration is connected, this project produces text
specifications, storyboards and panel-level prompts. Those are the inputs the art
step needs, so no work is wasted, but no artwork can be rendered from here.
