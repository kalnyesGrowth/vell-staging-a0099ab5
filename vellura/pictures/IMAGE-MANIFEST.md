# Image manifest — Vellura intake funnel

Per spec: pictures are exported to this folder, not left inside the Figma file, and each
one is marked FINAL or STAND-IN.

**Every image in this folder is a STAND-IN.** None are final. See "Art direction" below
for why the direction itself is a decision, not just a placeholder.

| File | Slot | Source | License | Status |
|---|---|---|---|---|
| `hero-texture.jpg` | Lander hero ground | Openverse (rawpixel) | **CC0** public domain | STAND-IN |
| `product-tube.png` | Hero SKU pack shot | Generated, Higgsfield `nano_banana_2` | Generated asset, no third-party rights | STAND-IN |
| `hands-cream.png` | Application step | Generated, Higgsfield `nano_banana_2` | Generated asset, no third-party rights | STAND-IN |
| `pharmacy.png` | Compounding / fulfilment section | Generated, Higgsfield `nano_banana_2` | Generated asset, no third-party rights | STAND-IN |
| `calm-fabric.png` | Neutral section ground | Generated, Higgsfield `nano_banana_2` | Generated asset, no third-party rights | STAND-IN |
| `toe-solution.png` | Toe fungus mini pack shot | Generated, Higgsfield `nano_banana_2` | Generated asset, no third-party rights | STAND-IN |

**Dosage form matters.** `toe-solution.png` is a dropper bottle, not a tube, because FP61 is
a solution in DMSO rather than a cream. The first pass reused the Vellura cream tube and it
was wrong: a cream pack shot on a nail-solution lander misrepresents the product before
anyone reads a word.

## Art direction: no faces. This is deliberate.

There is not a single photograph of a woman's face in this funnel, and that is a
compliance decision rather than an aesthetic one.

A stock model's face placed beside facial-hair-treatment copy does two things a regulator
reads badly. It implies she is a patient, which is an unpaid undisclosed endorsement
(FTC Endorsement Guides, and `compliance/checklist.md` §2). And in a category whose entire
promise is visible change, a "clear skin" face sitting next to the offer functions as an
implied before/after, which Meta prohibits outright (`checklist.md` §4).

So the visual system is: the product, the texture, the hands, the pharmacy. The face is
the one thing we never show.

**Consequence for launch:** final imagery needs a commissioned shoot with signed model
releases *and* explicit consent covering the condition context. That is a real line item.
It is listed in `WHATS-NOT-DECIDED.md`.

## Rejected during sourcing

Five CC0 photographs were pulled and then rejected on inspection. Recording them so nobody
re-sources the same mistakes:

- **Branded competitor tube** — a real "SKEYNDOR Urban White Spots Eraser Cream" pack shot.
  Third-party trademark, and the wrong indication (dark spots, not hair).
- **Retail pill bottles** — labels legible, one reading "BuPROPion Hydrochloride Extended
  Release". A named antidepressant in a hirsutism funnel is incongruent and a compliance
  hazard. We also ship a cream, not oral tablets.
- **Woman in towel with clay face mask** — the exact implied-patient face shot ruled out
  above, plus a different product category.
- **Camouflage upholstery swatches** — olive and grey, clashes with the entire palette.
- **Baby-blue hand cream flat lay** — palette fights the warm cream and plum system.

## Regeneration

`_build/fetch_images.py` re-pulls the CC0 slot. The generated assets came from
Higgsfield `nano_banana_2`, 1:1, 1k, one image per call. Prompts are recorded in
`_build/IMAGE-PROMPTS.md` so any of them can be re-rolled on-palette.
