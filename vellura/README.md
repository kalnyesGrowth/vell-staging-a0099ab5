# Vellura — dev-ready intake package

Female facial hair (hirsutism). Compounded 3-in-1 cream. Complete intake funnel, built as
mobile-390 HTML so it imports into Figma with real, selectable text.

## Why HTML and not hand-built Figma

The reference files are HTML imports themselves — the layers in the Sana file are literally
named `Bistra-mobile-390.html.html`. So this matches the house method rather than fighting
it, and it means every word arrives in Figma as live text a developer can copy, which is
the thing the brief asks for twice.

It also means the whole funnel regenerates from one content file. Changing the wait-time
promise, a price, or a claim is one edit and one command, not 70 frames of manual work.

## Import order

1. Open the target Figma file.
2. Run the **html.to.design** plugin, "Import web page" → "Upload HTML".
3. Import **`FULL-mobile-390.html` first.** That single file contains all 35 screens in
   both languages, in order, each with its code chip.
4. Then import the boards you want as separate pages: `decision-tree.html`,
   `SPEC-annotations.html`, `screen-necessity-map.html`, `design-tokens.html`,
   `toe-fungus-MINI.html`.
5. Fonts: Sentient and General Sans load from Fontshare. If the plugin cannot reach the
   CDN, install both locally first so text imports with correct metrics instead of
   falling back.

`screens/` holds one file per screen for anyone who wants a single frame in isolation.
You do not need them if you imported the FULL file.

## What is in here

| File | What it is |
|---|---|
| `FULL-mobile-390.html` | All 35 screens, EN + ES, in order. **Import this first** |
| `decision-tree.html` | If she presses this, what happens. Branches, stops, and what is kept at each stop |
| `SPEC-annotations.html` | Per screen: single or multi, branches or record-only, skippable, field rules, claims |
| `screen-necessity-map.html` | What is clinically required vs what exists to convert |
| `design-tokens.html` | Which colors matter and which are stand-ins. Fonts and their web licence |
| `toe-fungus-MINI.html` | Opportunity #2. Tree plus four hero screens |
| `index.html` | Hub page linking all of the above |
| `pictures/` | Exported images plus `IMAGE-MANIFEST.md`. Every one marked STAND-IN |
| `_build/` | The generator. Edit content here, re-run, re-import |

## Regenerating

```bash
cd _build && python3 build.py
```

No dependencies beyond Python 3.

| To change | Edit |
|---|---|
| Any words, EN or ES | `content.py` |
| Colors, fonts, spacing, type scale | `tokens.py` |
| Branch logic, field rules, screen states | `spec.py` |
| A claim or its source status | `claims.py` |
| Toe fungus mini package | `content_toe.py` |
| Layout of a component | `render.py` |

Every user-facing string is authored as a pair:

```python
L("A clinician wants a second look.",
  "Un profesional clínico quiere revisar con más calma.")
```

The funnel renders twice from one source, so a half-translated build is structurally
impossible rather than something QA has to catch.

## Reading the frames

- Dotted underline with a superscript code = a product claim. Source and status live in
  `_build/claims.py` and in the annotations.
- Yellow highlight = placeholder copy that needs a real value before launch.
- Grey chip = screen code. Purple chip = variant (ERROR, EMPTY, CONDITIONAL, ES).
- Bordered box with a left rule = legal copy, marked do-not-reword.

## The one thing worth knowing before you read anything else

**Only four questions branch the flow:** Q-01 (age), Q-07 (hormonal signs), Q-09
(pregnancy), Q-16 (state). Q-14 and Q-15 flag silently for clinician review without
interrupting her. **Every other question is recorded for the clinician and changes nothing
she sees.**

That is the answer to "does this answer change what she sees next, or is it just recorded,"
and it is the fact most likely to save build time.

## Not decided yet

See `../WHATS-NOT-DECIDED.md`. The short version: the pharmacy has not quoted the hero SKU,
the day-one state list is empty, the 24-hour review promise is a placeholder, and two
ingredient claims cannot ship until a clinician signs off on the wording.
