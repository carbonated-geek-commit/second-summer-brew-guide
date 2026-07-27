# Second Summer Brew Site — Claude Code Task Brief

> **How to use this file:** save it as `CLAUDE.md` in a fresh project directory. If the current build
> (`red-ipa-brew-guide.html`, exported from a prior session) is sitting next to it, run **Mode A**.
> If not, run **Mode B**. This file is the canonical source of truth for the project — when the page
> and this document disagree, this document wins.

## Mission

Ship a single-file static brew guide — "Second Summer": two brews, five beers — to GitHub Pages
under my account, then maintain it from this spec in future sessions.

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

### Calendars

- **Red:** brew Aug 1 → dry hop Aug 5 → FG stable Aug 11–13 → fruit Aug 14 → package Aug 18–24 →
  pouring Sept 1–7 → peak mid-September.
- **Blonde:** brew Aug 8 → free rise from Aug 11 → package Aug 18–22 → first pour mid-September →
  peak October.

---

## Site Spec (Mode B only)

- **One file**, `index.html`, HTML + CSS + JS inline. Only external resource: Google Fonts —
  Bricolage Grotesque (500/700/800, display), Instrument Sans (400/500/600, body), Spline Sans
  Mono (400/500/600, all measurements and gravity figures).
- **State machine:** `<html data-brew="red|blonde" data-path="classic|grapefruit|cherry|blackberry">`.
  Visibility is CSS-driven: `html[data-brew="blonde"] .red-only { display:none !important }` and the
  mirror rule for `.blonde-only`. Fork panels key off `data-path`. JS only toggles attributes and
  button states.
- **Tokens:** bg `#1C1113` · panel `#26161A` · text `#F3E9DB` · secondary `#C98E52` · hairline
  `rgba(243,233,219,.14)`. Accents — classic `#CB4F3C`, grapefruit `#EF6A5A`, cherry `#C63A55`,
  blackberry `#9A6BB4`, blonde `#D9A63C`. The accent and the CSS pint-glass gradient
  (`--beer-top` / `--beer-bottom`) both shift with state.
- **Structure, top to bottom:** sticky topbar (brew switcher; fruit chips are `.red-only`) → hero
  (CSS pint glass + six-cell vitals grid per brew) → fork ratings cards with pick buttons (red) →
  shopping lists → brew-day checklist → fermentation checklist → fork panels (red) → packaging +
  calendar → mono quick-reference block per brew.
- **Steps** are list items with large custom checkboxes (DOM state only — resets on reload, by
  design), duration badges, and amber "checkpoint" styling on the OG/FG gates.
- **Mobile-first:** single column, 720 px max width, clean at 380 px, respects
  `prefers-reduced-motion`.

## Acceptance checklist

- [ ] HTML parses with balanced tags and globally unique `id`s.
- [ ] Brew switcher toggles Red ⇄ Blonde; all four fruit paths render and recolor accent + glass.
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
