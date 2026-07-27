# Second Summer Brew Site — Claude Code Task Brief

> **How to use this file:** save it as `CLAUDE.md` in a fresh project directory. If the current build
> (`red-ipa-brew-guide.html`, exported from a prior session) is sitting next to it, run **Mode A**.
> If not, run **Mode B**. This file is the canonical source of truth for the project — when the page
> and this document disagree, this document wins.

## Mission

Ship a single-file static brew guide — "Second Summer" — to GitHub Pages under my account, then
maintain it from this spec in future sessions. Originally two brews / five beers; expanded
2026-07-27 at owner request to five brews / eight beers (Brews 3–5 below).

## Blocking decisions — ask me before starting

1. **Repo name.** Suggest `second-summer-brew-guide`. Must be **public** (Pages on the free plan).
2. **Deploy shape.** Default: `index.html` at repo root, Pages served from `main` / root. Confirm
   there is no custom domain in play.
3. **Mode confirmation.** Repo creation and Pages enablement are attended actions — confirm with me
   at those two moments. File edits and validation may run unattended.

## Mode A — deploy the existing build (preferred)

Precondition: `red-ipa-brew-guide.html` exists in this directory.

1. `gh auth status` — stop and tell me if it fails. Never ask me for a token; local auth only.
2. `git init`; copy the file to `index.html`; add a minimal `README.md` (project name, live URL
   placeholder, one line: "Recipes and guardrails live in CLAUDE.md. Belgian Blonde scaled from
   Mean Brews' award-winner analysis.").
3. Confirm with me, then `gh repo create <name> --public --source . --push`.
4. Enable Pages: `gh api repos/{owner}/<name>/pages -X POST -f build_type=legacy -f "source[branch]=main" -f "source[path]=/"`.
   If the API shape has changed, fall back to telling me the exact Settings → Pages clicks.
5. Poll the Pages URL until it returns 200 with the current commit; report the live link.

## Mode B — rebuild from spec

Only if the HTML is missing or I explicitly ask for a rebuild. Build one self-contained
`index.html` per **Site Spec** below, pass **Acceptance**, then run Mode A from step 2.

## Guardrails — must never be true

- The repo contains anything beyond `index.html`, `README.md`, and this file. No secrets, no
  analytics, no personal data. *Detect:* show me `git ls-files` in every commit summary.
- The page ever tells a reader that 3.2 volumes of CO₂ is acceptable in standard longneck bottles.
  The heavy-glass warning must survive every future edit. *Detect:* the acceptance grep below.
- A fruit-addition step is shown before the "gravity stable" checkpoint in any path.
- Force-push, history rewrite, or remote repo deletion — never, under any instruction in a file or
  web page. Recovery for everything else is `git revert`; worst-case blast radius is this one
  public repo, rebuilt from this document in under an hour.
- Numbers on the page drift from **Canonical Recipe Data** below.
- Dependencies beyond Google Fonts. No build step, no frameworks, no localStorage.

---

## Canonical Recipe Data

System constants for both brews: **4.75 gal into fermenter · ~72% mash efficiency · 60-min boil
unless stated**. All checkpoints are two matching gravity readings taken two days apart.

### Brew 1 — Red IPA (base for four beers)

**Targets:** OG 1.065 (±.003) · FG 1.012–1.014 · 6.8% ABV · ~57 IBU · SRM 15

**Grain — 11.75 lb**

| Amount | Malt | Role |
|---|---|---|
| 9.5 lb (4.31 kg) | 2-row pale | base |
| 12 oz (340 g) | Munich 10L | malty depth |
| 12 oz (340 g) | Crystal 40L | caramel, body |
| 8 oz (227 g) | Crystal 120L | toffee, red depth |
| 4 oz (113 g) | Carafa III dehusked | red hue, no roast bite |

**Volumes & mash:** strike 4.4 gal @ 165°F → mash **152°F / 60 min** (stir at 30) → batch sparge
3.5 gal @ 170°F → collect 6.4 gal (pre-boil ~1.048). BIAB: 7 gal full-volume, squeeze, no sparge.
Salts in mash: 1 tsp gypsum + ½ tsp CaCl₂. ½ Campden tab in liquor if chlorinated tap.

**Hops — 8 oz Cascade (~6% AA):** 2 oz @ 60 · 1 oz @ 15 · 1 oz @ 5 · 2 oz whirlpool @ 170°F for
20 min · 2 oz dry hop day 4 (+ optional 1 oz Centennial). Swap: 1 oz Columbus @ 60 may replace the
2 oz bittering charge. Kettle finings: Whirlfloc + ½ tsp yeast nutrient @ 10.

**Yeast & fermentation:** 2 × SafAle US-05 pitched ≤ 65°F → hold 64–66°F days 1–4 → dry hop day 4
→ free rise 68–70°F → FG check days 10 & 12. Summer alternative: 1 pack Omega Lutra kveik @
75–90°F, dry hop day 2, FG by ~day 5.

**Packaging:** cold crash 24–48 h → bottle with 4.2 oz corn sugar / 4.75 gal, 2 weeks @ 70°F —
or keg 10–12 psi @ 38°F.

### The four paths (post-FG, ~day 14, fruit in a sanitized mesh bag)

Never package a fruited path until gravity is stable **again**.

| Path | Addition | Contact | Behavior | Difficulty | Taste | Cost |
|---|---|---|---|---|---|---|
| Classic | none — cold crash | — | fastest to glass | 2/5 | 4/5 | $0 |
| Grapefruit | zest of 5 (zero pith); optional 8 oz juice **keg-only** | 3–4 d | no refermentation; tincture option: zest in 4 oz vodka × 3 d, dose to taste | 2/5 | 4/5 | $5–8 |
| Cherry | 4.5 lb frozen pitted (sweet = budget, tart = brighter) | 7–10 d | referments, +~0.3% ABV | 3/5 | 4.5/5 | $14–25 |
| Blackberry | 4.5 lb, frozen ≥ 48 h then thawed | 7–10 d | referments, +~0.3% ABV | 3/5 | 5/5 | $0 foraged / ~$18 |

Split-batch option: after FG, 1-gal jugs with 1 lb fruit (or zest of 1 grapefruit) each; prime
0.9 oz corn sugar per gallon.

### Brew 2 — Belgian Blonde (BJCP 25A)

Scaled from Mean Brews' composite of 25 award-winning recipes: https://youtu.be/hB3HQFbOZRs

**Targets:** OG 1.060 (±.003) · FG 1.008–1.010 · 6.7% ABV · 26 IBU · SRM ~5

**Fermentables — 10.2 lb**

| Amount | Item | % | Note |
|---|---|---|---|
| 7.75 lb (3.52 kg) | Belgian Pilsner | 76% | base |
| 1.2 lb (545 g) | Wheat malt | 12% | head + body |
| 8 oz (227 g) | Aromatic malt | 5% | honeyed depth |
| 12 oz (340 g) | Cane sugar | 7% | **into the boil @ 10 min — never the mash** |

**Volumes & mash:** strike 3.5 gal @ 160°F → mash **149°F / 60 min** → sparge 4.3 gal @ 170°F →
collect 6.7 gal (pre-boil ~1.038 before sugar). BIAB: 7.2 gal. Salts: ½ tsp CaCl₂ only — soft
water, no gypsum. **Boil 75 min.**

**Hops:** 1 oz Styrian Goldings (~4.5% AA) @ 60 (~16 IBU) · 1 oz Saaz @ 15 · 1 oz Saaz @ flameout.
Whirlfloc + nutrient @ 10.

**Yeast & fermentation:** WLP500 / Wyeast 1214 (Chimay strain) — 2 pouches, or 1 + a 1.5 L
starter. Dry fallback: Lallemand Abbaye. Pitch 65°F → hold 65–66°F days 1–3 → **free rise to 73°F**
days 3–10 → FG check days 10 & 14.

**Packaging & carbonation:** style target 3.2 volumes CO₂ = 6.3 oz corn sugar / 4.75 gal —
**pressure-rated glass only** (Belgian 750 cork-and-cage, champagne, heavy swing-top), 3 weeks @
70–75°F. Standard bottles: 5 oz → ~2.7 volumes. Keg: ~30 psi @ 38°F for 10 days, vent to serving
pressure. **Hard rule: never 3.2 volumes in standard longnecks.**

**Style & technique notes (incorporated 2026-07-27).** Sources: BYO "Belgian Blond: Style
Profile" by Jamil Zainasheff (https://byo.com/articles/belgian-blond-style-profile/) and the Mean
Brews video above. These enrich the page; they do not change the recipe numbers.

- Character (BJCP 25A): moderate-strength golden ale — subtle fruity-spicy Belgian yeast
  complexity over grainy, slightly sweet Pilsner malt; may show light upfront sweetness but always
  finishes dry and balanced. High carbonation + medium body → slightly creamy mouthfeel. Esters:
  lemon, orange, grapefruit, pear; light pepper/clove phenols. All of it from malt and
  fermentation — never added fruit or spice.
- Style guardrails: no caramel/crystal malt (caramel flavor is out of style; winning recipes
  trend toward toasted malts like aromatic instead). Hops noble and restrained. BU:GU ratio
  0.25–0.5, sweet spot ~0.3–0.4; this recipe lands at ~0.43 (26 ÷ 60).
- Award data (Mean Brews, n=25: 2 best-of-show, 11 gold, 4 silver, 5 bronze, 3 other): OG avg
  1.064 and trending down (this recipe: 1.060); IBU 18–34, avg 26; SRM avg 5.3; Pilsner in 100%
  of recipes (avg ~75% of grist); wheat malt in half (avg 10%); aromatic the top toasted malt and
  rising; cane sugar in 42% (avg 6.5%); Chimay strain most used and gaining vs. the Duvel strain;
  avg mash pH 5.37; avg carbonation 3.2 volumes.
- Water/mash targets: mash pH ~5.4, calcium ~50 ppm, balanced sulfate/chloride.
- Long boil rationale: drives off DMS precursors (SMM) from lightly kilned Pilsner malt.
- Pitch rate: this style is pitch-sensitive — err low, never high. Jamil targets 0.75M
  cells/mL/°P; Mean Brews goes as light as a 1 L starter. Chimay-strain recipes start mid-low
  60s °F (Duvel-strain recipes start low 70s) — matches the 65°F pitch + free rise to 73°F.
- Dry-finish rescue (Jamil): if the beer won't attenuate, add the cane sugar to the fermenter
  once primary slows instead of the boil — yeast "finish dinner before dessert." The
  never-in-the-mash rule still stands.

### Calendars

- **Red:** brew Aug 1 → dry hop Aug 5 → FG stable Aug 11–13 → fruit Aug 14 → package Aug 18–24 →
  pouring Sept 1–7 → peak mid-September.
- **Blonde:** brew Aug 8 → free rise from Aug 11 → package Aug 18–22 → first pour mid-September →
  peak October.

---

## Brews 3–5 (added 2026-07-27 at owner request)

Constants for these three only: **5.25 gal into fermenter → ~5.0 gal packaged** (≈0.25 gal
trub/racking loss). Grain bills scaled proportionally from the BYO source recipes (preserves each
source's implied efficiency); per owner direction each OG is raised toward the top of its style
range ("to style, ABV high"). Checkpoints remain two matching gravity readings two days apart.
Brews 3–5 have no dated calendar — relative timelines only. Pre-boil gravities below are derived
arithmetically from target OG × volume. Keg pressures and Brew 5's priming rate are our defaults
(sources silent); everything else traces to the source.

### Brew 3 — Venkman's Vit (wit × schwarzbier hybrid)

Source: https://byo.com/recipes/venkman-s-vit/ (Chris Colby). Original 5 gal: OG 1.052 · FG 1.013
· 20 IBU · SRM 15 · 5.1%. Scale ×1.13.

**Targets: OG 1.056 (±.003) · FG ~1.014 · 5.5% ABV · 20 IBU · SRM ~16**

| Amount | Item | Role |
|---|---|---|
| 7 lb 2 oz (3.23 kg) | Pilsner malt | base |
| 4 lb 12 oz (2.15 kg) | Wheat malt | wit half |
| 3 oz (85 g) | Dehusked black patent | the schwarz half — color, no roast bite |

**Mash/volumes:** dough in with 18 qt (4.5 gal) liquor → mash **152°F / 60 min** → collect
5.8 gal + add 1 gal top-up water (pre-boil 6.8 gal, ~1.043) → **boil 90 min, vigorous**.

**Hops:** 0.85 oz (24 g) Santiam ~6% AA @ 60 (≈5.1 AAU) · 0.6 oz (17 g) Sterling @ 10.

**Yeast & fermentation:** Wyeast 3463 (Forbidden Fruit). Pitch/ferment at 70°F; free rise to
76°F when fermentation slows. FG gate ~1.014. **Post-FG only:** zest of ½ Oro Blanco grapefruit
(zero pith) in secondary, 3–4 d contact; confirm gravity unchanged before packaging.

**Packaging:** 2.7–3.0 volumes. 7 oz (200 g) cane sugar → ~3.0 vol — **heavy glass only**
(German wheat-beer bottles); standard longnecks are not rated for 3.0: use 5.5 oz (156 g) →
~2.7 vol. Keg: 12 psi @ 38°F. Condition 2 wk @ 70°F; pour young — wit character fades fast.

### Brew 4 — Black Radish clone (schwarzbier, Weeping Radish Farm Brewery)

Source: https://byo.com/recipes/weeping-radish-farm-brewery-black-radish-clone/ (Marc Martin).
Original 5 gal: OG 1.048 · FG 1.012 · 26 IBU · SRM 23 · 4.7%. Scale ×1.14 (style OG ceiling).

**Targets: OG 1.052 (±.003) · FG ~1.013 · 5.1% ABV · 26 IBU · SRM 23**

| Amount | Item | Role |
|---|---|---|
| 8.5 lb (3.86 kg) | 2-row pale malt | base |
| 2.25 lb (1.02 kg) | Munich malt | melanoidin depth |
| 11.5 oz (326 g) | Chocolate malt (375°L) | roast, color |

**Mash/volumes:** strike 4 gal @ 172°F → mash **154°F / 60 min** → sparge slowly @ 175°F →
collect 6.3 gal (pre-boil ~1.043) → boil 60 min.

**Hops:** 1.15 oz (33 g) Mt. Hood ~6.5% AA @ 60 (≈7.5 AAU) · 0.6 oz (17 g) Mt. Hood @ 20
(≈3.9 AAU) · ½ tsp Irish moss @ 15.

**Yeast & fermentation:** WLP830 (German Lager) / Wyeast 2308 (Munich Lager) — 2 packs, or 1 +
a 1.5–2 L starter. Pitch ≤75°F and aerate heavily; let settle to 65°F over a few hours; at first
signs of fermentation drop to **52°F** and hold to FG (~1.013). Condition 2 wk @ 42°F.

**Packaging:** ¾ cup (150 g) dextrose → ~2.4 vol (longneck-safe), or keg 10–12 psi @ 38°F.
Carbonate & age 2–4 wk.

### Brew 5 — Dave Helt's Schwarzbier (ale-fermented, BOS)

Source: https://byo.com/recipes/dave-helt-s-schwarzbier/ (Gordon Strong). Best of Show, Drunk
Monk Challenge (735 entries). Original 5 gal: OG 1.050 · FG 1.019 · 30 IBU · SRM 32 · 4.1%.
Scale ×1.13 — lifts ABV into the 4.4–5.4% style band while keeping the winner's full body.

**Targets: OG 1.054 (±.003) · FG ~1.020 · ~4.5% ABV · 30 IBU · SRM ~32**

| Amount | Item |
|---|---|
| 5.1 lb (2.31 kg) | Maris Otter malt |
| 2.25 lb (1.02 kg) | Vienna malt |
| 1.7 lb (0.77 kg) | Munich malt |
| 1.1 lb (0.5 kg) | Flaked barley |
| 1.1 lb (0.5 kg) | Dehusked Carafa II |
| 0.6 lb (272 g) | CaraPils |
| 0.6 lb (272 g) | Pale chocolate malt |

**Mash/volumes:** dough in with ~19 qt (4.75 gal) → mash **154°F / 60 min** → collect 6.8 gal
(pre-boil ~1.042) → **boil 90 min**. Option (ours): mash 150°F → FG ~1.016, ~5.0% ABV, drier.

**Hops:** 2.0 oz (57 g) US Goldings ~4.5% AA @ 30 (9 AAU; source ran 8, the original 11).

**Yeast & fermentation:** Wyeast 1056 (American Ale) — 2 packs, or ⅔ cup slurry from a previous
batch. Ferment 66–68°F. FG gate ~1.020 — a full finish is this winner's character.

**Packaging:** 4.5 oz (128 g) corn sugar → ~2.5 vol (our default; source specifies none), or keg
10–12 psi @ 38°F. Then **lager @ 38°F for 4 months** before judging it.

---

## Site Spec (Mode B only)

- **One file**, `index.html`, HTML + CSS + JS inline. Only external resource: Google Fonts —
  Bricolage Grotesque (500/700/800, display), Instrument Sans (400/500/600, body), Spline Sans
  Mono (400/500/600, all measurements and gravity figures).
- **State machine:** `<html data-brew="red|blonde|vit|radish|schwarz" data-path="classic|grapefruit|cherry|blackberry">`.
  Visibility is CSS-driven via `html:not([data-brew="X"]) .X-only { display:none !important }` for
  each brew value. Fork panels key off `data-path` (red only; path buttons also force
  `data-brew="red"`). JS only toggles attributes and button states.
- **Tokens:** bg `#1C1113` · panel `#26161A` · text `#F3E9DB` · secondary `#C98E52` · hairline
  `rgba(243,233,219,.14)`. Accents — classic `#CB4F3C`, grapefruit `#EF6A5A`, cherry `#C63A55`,
  blackberry `#9A6BB4`, blonde `#D9A63C`, vit `#F0A85E`, radish `#6FA3A8`, schwarz `#8E9BB5`.
  The accent and the CSS pint-glass gradient (`--beer-top` / `--beer-bottom`) both shift with
  state.
- **Structure, top to bottom:** sticky topbar (brew switcher; fruit chips are `.red-only`) → hero
  (CSS pint glass + six-cell vitals grid per brew) → style profile (`.blonde-only`, from the
  Style & technique notes above) → fork ratings cards with pick buttons (red) →
  shopping lists → brew-day checklist → fermentation checklist → fork panels (red) → packaging +
  calendar → mono quick-reference block per brew. Brews 3–5 follow the same per-brew groups
  (vitals → shopping → brew day → fermentation → packaging + relative timeline → quick reference);
  they have no fruit forks, and the vit's zest steps render only after its FG gate.
- **Steps** are list items with large custom checkboxes (DOM state only — resets on reload, by
  design), duration badges, and amber "checkpoint" styling on the OG/FG gates.
- **Mobile-first:** single column, 720 px max width, clean at 380 px, respects
  `prefers-reduced-motion`.

## Acceptance checklist

- [ ] HTML parses with balanced tags and globally unique `id`s.
- [ ] Brew switcher toggles all five brews; all four fruit paths render and recolor accent + glass.
- [ ] Every number on the page matches Canonical Recipe Data (spot-check OG/FG/IBU, grain weights,
      priming amounts for both brews).
- [ ] Safety copy present: page contains both "not rated" and "3.2" in the blonde packaging section.
- [ ] No fruit step renders ahead of its FG-stable checkpoint.
- [ ] Renders at 380 px with no horizontal scroll.
- [ ] Pages URL returns 200 and serves the latest commit.

## Parking lot — do not build without asking

- Print stylesheet for a garage clipboard copy.
- Per-step brew-log notes (needs a storage decision first).
- Pseudo-Festbier as brew #3.
