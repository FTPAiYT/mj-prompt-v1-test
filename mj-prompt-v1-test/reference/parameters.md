# Parameters — the levers

The knobs that reshape a Midjourney prompt. Curated from a working creator's note vault (~v6/v7 era, 2025).

**How to read the flags**
- 🟢 = durable. The concept holds across versions; trust it.
- 🟡 = volatile. A default value, a range, or a version-specific behavior. **Midjourney changes fast — re-check these before quoting them as gospel.**

**Universal mechanics** (🟢)
- Parameters start with `--`, go at the **end** of the prompt, after your words.
- **Order among parameters doesn't matter:** `--c 6 --s 400` == `--s 400 --c 6`.
- **Decimals work** in most numeric params (`--s 0.25`, `--iw 1.2`).

---

## The two questions every parameter answers

Almost all of this page collapses into two creative decisions:

1. **How literal vs. how pretty?** → `--s` (stylize) and `--style raw`. MJ defaults to making things beautiful; these dial that instinct up or down.
2. **How same vs. how varied?** → `--c` (chaos), `--weird`, and permutations decide how different your four grid images are from each other.

Everything else is references, framing, speed, and exclusion.

---

## Stylize — `--s` (the main lever)

🟢 Controls how much **influence / personality / "creative freedom"** the bot exerts over your words. Two equivalent framings, both worth keeping:
- **Beauty vs. accuracy:** MJ leans toward conventional beauty. Higher `--s` = prettier but drifts from your prompt; lower = more faithful to exactly what you typed, but can get plain or ugly.
- **The bot's taste vs. yours:** the model is reinforced with beauty ratings, so at high `--s` the bot makes what *it* thinks is the best-looking version of your prompt.

🟡 **Default 100. Range 0–1000.** (Legacy/historical only: v3 defaulted to 2500 with a much larger range — up to 60000; test/testp models accepted roughly 1250–5000. Ignore unless prompting an old version.)

🟢 **Usage map from a creator who ran 62,000+ prompts** — concrete starting points (the notes recommend the default 100 as the best balance of beauty and accuracy, and to sweep values like 100 / 400 / 650 / 1000 when exploring):
- Default **100** is the everyday balance — most prompts are fine here.
- Nudge **up** (e.g. 200–400+) when you want it prettier / more "the bot's taste."
- Drop **toward 0** when you're fighting for accuracy / concept fidelity.

🟢 **How to move it:**
- Want it a touch prettier? Raise it.
- Fighting for accuracy / concept fidelity? Lower it; last resort `--s 0`.
- A camera angle or odd composition won't render? Try lowering `--s` (the notes use values like `--s 30`–`40`) — high stylize can override literal instructions.

🟡 **Gotchas:**
- The tradeoff is real: more beauty = less accuracy. There is no free lunch.
- When a **personalization profile (`--p`)** or **mood board** is active, `--s` governs the strength of *your* board's influence, not MJ's generic taste.
- Try the literal **word "stylized"** in the prompt for an artistic look — note it's not repeatable like the parameter.

---

## Style raw + the realism formula — `--style raw` / `--raw`

🟢 A second, **less opinionated** model — "a slightly more boring older brother or sister." Two effects:
1. It follows your prompt **more closely** (stops silently adding flourishes to beautify short prompts).
2. It **favors realism / photographic** results over illustration.

🟢 **The realism formula: `--raw --s 0`.** Raw pushes toward reality; stylize 0 strips the bot's artistic instinct entirely. ⚠️ This is *also* the recipe for "ugly"/unflattering output — it shows you reality, warts and all.

🟢 **Order of operations for an accuracy/realism problem:** first lower `--s` → then add `--style raw` → then combine both → then go to `--s 0`.

🟢 **Gotchas / tips:**
- Raw needs **more prompt**: because it won't auto-beautify, short prompts come out plain. Add explicit "stunning / gorgeous" words if you want beauty *and* literalness.
- Pairs with the magic word **`unsplash`** for photorealism (e.g. `... unsplash --style raw`).
- Good for retexturing/style-transfer (lower stylize when doing those).
- Common example: `a woman in a red dress, the woman has green hair, the woman is wearing purple shoes, there is a white dog by her side --style raw` renders realistic where default MJ would illustrate it.

🟡 **`--rawtest` is not a Midjourney flag** — in this vault it's the creator's own custom shortcut (set via `/prefer option set`) that expands into the permutation `{,--style raw}`, i.e. it runs the prompt twice, with and without raw. Some older syntaxes for it stopped working; the actual flag is `--style raw` (or just `--raw`).

---

## Chaos — `--c` (variety across the grid)

🟢 Increases how **different the 4 grid images are from each other**. The fix when your grid is too samey. (Distinct from stylize: chaos changes *composition*; stylize drifts the *look*.)

🟡 **Range 0–100. Default 0.** (Legacy v3 used 0–1000, and there chaos meant "stray from the prompt," not "grid variety.")
- **3–6** = a light, frequent touch (a favorite "if I could only keep one parameter" pick).
- For "big game hunting" the notes call the sweet spot roughly **6–9 (±a couple)**.
- **50, 100** = wild — surfaces MJ's full range but gets ugly/nonsensical; use sparingly.

🟢 **Gotchas / tips:**
- The in-app **slider steps by 5**, which is often too coarse — type the value manually for finer control.
- The **remix-chaos trick:** turn Remix on, push HIGH chaos into a variation to explode options, then remove the chaos to settle on one.
- Pairs extremely well with **style references (`--sref`)** and mood boards.
- Use chaos in **Relax mode** to brainstorm without burning fast hours.

---

## Weird — `--weird` / `--w` (novelty engine)

🟢 Follows your prompt but makes things **strange** — a dice-roll for discovering *novel* styles (different axis from chaos's "spread").

🟡 **Range 0–3000. Default 0.** Use sparingly.
- **`--weird 1`** is called out as underrated ("weird 1 is the truth") — meaningful even at the floor.
- Values like **300–600** are used for active style-hunting (e.g. `--weird 300`, `--weird 600`).

🟢 **The style-discovery loop:** generate with a bumped weird value → upscale the cool ones → run `/describe` on them to mine the novel phrasing → you've minted a new style. Or: generate weird, then *erase* the weird value and Remix to refine the look.

🟡 The `--w` shorthand is version-specific (Niji often uses `--w`).

---

## Seed — `--seed` (for TESTING, not consistency)

🟢 The **starting blueprint** (the field of visual noise a generation grows from). Same prompt + same seed + same version ≈ the same image. By default MJ picks a random seed for you.

🟡 **Range 0 to 4,294,967,295** (~4.29 billion). Default is random.

🟢 **THE key gotcha — seeds give repeatability, NOT consistency:**
- A seed reproduces *that exact generation*. The moment you change **any** word, you access a brand-new blueprint — so a seed will **not** carry a character or style across different prompts.
- The seed is tied to the *full* prompt you wrote — e.g. you can't recreate an "angry royal guard" image without the word "angry" in it.
- For consistency, use **image prompts / character references / mood boards**, never a seed.

🟢 **What seeds are actually for — isolating one variable (the most scientific test in MJ):**
1. Lock a seed.
2. Run the prompt **with** a word.
3. Run it again **without** that word (use the `{,word}` permutation — see below).
4. Compare. Now you can *see* exactly what that word/parameter does, with no random noise confounding the result.
- Test example: `{fish eye lens, wide angle lens} ... --seed 357385279` isolates how each lens term behaves.
- If a word changes the four images but with no clear improvement, it isn't earning its place; if it produces a consistent, visible change, keep it.

🟢 **The reroll trap:** hitting **Reroll** on a seeded job silently assigns a **new random seed** (even though Discord may still display the old `--seed` number). To genuinely re-run the same seed, **re-enter the whole prompt** — don't reroll.

🟡 **Getting a seed:** in Discord, react to the grid with the ✉️ envelope emoji (react, don't reply) → the bot DMs the seed + job ID. (Mechanic is UI/version-specific.)

---

## Negatives — `--no` and `::` weighting

Two ways to push things *out* of an image.

### `--no` (exclude a thing)
🟢 `--no <thing>` removes or suppresses it. Cleanest for items with a strong default color/shape.
- `--no camera` — stop a subject staring into the lens (great with "paparazzi"/candid prompts; the notes pair it with polaroid/dslr shots).
- `--no mockup` — get the design itself, not a photo of a framed/mounted product (t-shirts, posters); also kills frames when you've mentioned "painting."
- `--no shadow` — for fonts/logos, so elements separate cleanly afterward.
- `--no ears`, `--no text`, `--no border`, `--no blur` — all reported working.

🟡 **Gotcha:** the notes describe the `--no` weight as roughly **1**, and it **doesn't always obey** — `jungle --no green` "will not work the way you think it will." When `--no` fails, reach for an explicit negative weight (below) for finer control. Describe what a thing *looks like* rather than negating a defining part (the notes' example: asking for "unicorn" forces a rainbow color unless you cancel it out).

### `::` multi-prompt weighting (incl. negatives)
🟢 `::` splits a prompt into weighted chunks. **No space between `::` and its number** (`word::5`, not `word:: 5`). Weights are **relative** (`tulips:: red::-.5` == `tulips::2 red::-1` == `tulips::200 red::-100`).
- **Positive:** `grandfather::8 clock::1` makes the grandfather dominate; flip the weights to flip dominance.
- **Negative:** put a minus sign to push a concept *away* — `neon colors::5 black and white drawing::-1` yields all neon, zero B&W. Negative-weighting an *antonym* can deepen a mood (`dark and broody:: happiness::-100`).
- **Negative-prompt an artist / concept progressively:** `starry night, abstract oil painting::100 van gogh::-100`, then escalate (`::150 van gogh::-100 mockup::-49`).
- **Remove unwanted color in a style:** after picking a style, e.g. `--no orange` in neon, or `--no red` for pop art (the notes' "tulips" example for color removal).

🟢 **The hard rule:** the **sum of all weights must be positive**, or you get *"The sum of all of the prompt weights must be positive."* The overall prompt has to stay net-positive even when subtracting pieces.

🟡 **Gotchas:** fractional "light touches" are unreliable (`a walnut in a forest :: neon .5` was logged in the notes as *not working*); rerolling weighted multi-prompts a few times is often "the key." (For *images*, use `--iw`, not `::`.)

---

## Reference weights — `--sw`, `--cw`, `--iw`, `--ow`

How strongly each kind of reference pulls on the result. (The references themselves — `--sref`, `--cref`, `--oref`, image prompts — live in the consistency/references material; this is just the *weight* knob for each.)

### Style weight — `--sw` (strength of a style reference `--sref`)
🟡 **Default 100. Range 0–1000.**
- Raise toward **1000** to let the style fully dominate; lower to let your subject/prompt details show through.
- Lower it when a sref's **color is overpowering** your changes.
- `--sw 0` effectively does nothing — go higher.

### Character weight — `--cw` (strength of a character reference `--cref`)
🟡 **Default 100. Range 0–100.**
- **`--cw 100` (default)** tries to carry over **face, hair, and clothes** — which is why a referenced character keeps "the clothes." Use it when you *want* the whole outfit to carry over.
- **`--cw 0`** focuses on the **face only** — the right choice for putting a character in new outfits/scenes. Many creators just sit at 0; you can also get away with somewhere around **10–30**.
- 🟢 **Reality check: `--cw` is a weak lever** — `--cw 0` vs `--cw 15` on the same seed barely differ. Don't expect miracles.

### Image weight — `--iw` (strength of an image prompt)
🟡 **Range 0–3 (v6/v7 — the v5 era was 0.5–2); default 1.**
- **~0.5** = treat the image as a loose concept, let text drive.
- **1.0** ≈ image and text weighted evenly.
- **2–3** = recreate the reference closely (used to reproduce a found image: `/describe` + `--style raw` + low `--s` + `--iw 3`).
- 🟡 Old folklore that "image at the front of the prompt = more picture, at the back = more prompt" is flagged in the notes as a **myth** — use `--iw`. (Per-image weights via `URL::value` became possible in newer versions.)

### Omni weight — `--ow` (strength of an omni-reference `--oref`, v7)
🟡 **Default 100. Range 1–1000.** A v7 feature; behavior is rough — increasing it past 100 tends *not* to help, and the notes warn there's "no fool-proof setting."
- Keep near **100**; the notes find lowering toward **~60** works fairly well for faces/characters (a tested shortcut sweeps `--ow {50,75,120}`).
- **Below 100** targets a board's *style*; **above 100** drags in everything in the reference combined with the board's aesthetic.
- For **objects**, raising `--ow` is worth trying (lowering it can warp the object). Some references break at any `--ow` change.

---

## Aspect ratio — `--ar` (try MANY, don't anchor on one)

🟢 Written `width:height`: `--ar 16:9` wide, `--ar 9:16` / `--ar 2:3` tall, `--ar 1:1` square (the default). Goes at the **end** of the prompt.

🟢 **Ratios are relative** — `10:5` = `2:1`, `6:9` = `2:3`. No need for big numbers.

🟢 **Pixel dimensions = a ratio.** You can type dims directly (e.g. a `940px × 335px` banner as `940:335`) and MJ converts them to the equivalent aspect ratio. Outputs **round to the nearest 32-pixel value**, so `16:9` / `4:5` come out *slightly* off and "parse back" differently through `/describe`.

🟢 **The actual principle — changing the frame can transform a generation.** If results are off, **the first thing to change is the aspect ratio.** A prompt can shine in square and fail wide. So:
- Match the subject to the space (a car → wide; a tree/full-body → tall like `2:3`)…
- …**but also run the *same* prompt across several ratios** and compare. Going *against* the grain (a vertical cinematic still, a wide polaroid) is a deliberate technique.
- ⚠️ **Not a rule:** specific favorites like `3:2` or `16:9` are just one creator's preferences in a given moment, not numbers to memorize. Don't anchor.

🟢 **Square-first workflow:** square (`1:1`) often gives the most accurate style/composition — generate there, then **expand to your target ratio in the editor** rather than generating wide from the start.

🟡 **Gotchas:** not every ratio is available in every version (older versions historically capped each side relative to the other, and very old versions only allowed a couple of ratios ⚠️ unverified specifics). When making **video**, set the ratio *before* animating — you can't reliably reframe mid-process.

---

## Speed & quality — `--draft`, `--q`, `--hd`, `--exp`, `--repeat`

### Draft mode — `--draft`
🟡 Introduced in v7. **~1/4 the cost** of a normal generation, with a mild quality drop — great for high-volume exploration. ⚠️ **Only the first generation is draft-priced; variations cost full price.**
- Note: there are *two* things called "draft" — the `--draft` flag (cheap/fast) and the conversational **Draft Mode** UI (talk to MJ in plain language). They behave differently. To rescue a specific draft image, grab its **seed** and rerun in standard mode. (Get out of draft mode for anything fighting blur.)

### Quality — `--q` / `--quality`
🟡 **Range 0.25–2 (some eras up to 4–5). Default 1.**
- `--q 0.25` = rough, ~4× faster/cheaper; `--q 0.5` ~2× faster — ideal for **hunting composition/colors** before you care about detail.
- `--q 2` = ~2× slower and ~2× the price, more detail — for keepers.
- People forget it exists; raise it to fight blur.

### HD — `--hd`
🟡 A different, higher-res algorithm; slower. Often bundled in a `--wallpaper`-style shortcut. (Better for larger/abstract/landscape images but less consistent composition. ⚠️ unverified description.)

### Experimental — `--exp`
🟡 v7-era. Adds detail/variety; "it's the truth — keep it low." Used low in the notes (e.g. `--exp 10`, `--exp 14`); pairs well with `--style raw`; can hurt accuracy if pushed. ("Don't forget `--exp`.")

### Repeat — `--repeat`
🟡 Runs the same prompt several times at once — fast style exploration, especially with `--sref random`. The notes say up to ~34; **5–10** is practical. May require fast hours.

---

## Permutations — `{ }` (the testing workhorse)

🟢 Curly brackets run **many prompts at once** from one line. The single best tool for testing parameters and isolating variables.
- **List:** `a {red, blue, green} coat` → 3 jobs.
- **With/without a word:** `{,word}` → runs the prompt *with* and *without* it. Combined with a **locked seed**, this is the most scientific A/B test in Midjourney.
- **Parameters too:** `--s {40,100,400}` sweeps stylize; `{--niji 5 --style expressive, --niji 5}` compares models.
- **They multiply:** `a {dog,cat} --s {50,400} --ar {1:1,2:3}` = 2 × 2 × 2 = **8** jobs.
- **Weights/sliders:** `horns::{-0.1,-0.3,-0.5}` sweeps a weight (remember: **no space** before `{`).
- **Escape literal commas** inside a value with a backslash: only the *un-escaped* comma divides options.

🟡 **Limits & gotchas:** permutations **don't run in Relax mode**; expansion is capped at a maximum number of prompts (the exact cap, and a lower cap for non-Pro accounts, ⚠️ unverified). The classic mistakes: a space after `--s {`, using `.` instead of `,`, a wrong `\,` escape, permuting *subjects* when you meant to test styles/ratios/params, and trying it in Relax.

---

## Other flags worth knowing (mostly 🟡 — version-specific)

- **`--v` / version** — `--v 6`, `--v 6.1`, `--v 7`, etc. Pick the model. Test across versions with a locked seed: `--v {6,6.1,7}`. Old versions still produce distinct, sometimes-beautiful looks (a reason people remix *into* old versions for uniqueness).
- **`--niji`** — the anime/illustration model (`--niji 5/6/7`, with `--style expressive`/`scenic`/`cute`). Try anything you do in MJ in Niji too; `--style raw` works in Niji to de-anime it. (It can run on an older ranking/sref system, so codes don't always sync. ⚠️ unverified.)
- **`--style random`** — random style each run; great with `--repeat`. Variants control the pool size/percentage: `--style random-128` uses a 128-length tuner, and `--style random-128-50` looks at ~50% of that set (`random-128-40` = 40% of 128 pairs).
- **`--tile`** — seamless, repeatable textures/patterns (works best at `1:1`). You can click a tiled result a couple of times to preview it surrounding itself instead of using a seam checker.
- **`--stop`** — halt generation early at a percentage (`--stop 80`, valid 10–100); the last **10–20%** adds detail/sharpness, so stopping early gives a softer/unfinished look. You can't `--stop` an upscale.
- **`/prefer option set` (Discord shortcuts)** — bake a name into a bundle of params/words, e.g. `--wide` → `--ar 16:9`. Permutations can live inside shortcuts and vice-versa (e.g. a `--rawtest` shortcut expanding to `{,--style raw}`).

---

## Quick reference

| Flag | What it does | Range / default | Freshness |
|---|---|---|---|
| `--s` / `--stylize` | beauty/personality vs. prompt accuracy | 0–1000, default **100** | 🟡 range/default |
| `--style raw` (`--raw`) | less opinionated; literal + realistic | flag | 🟢 |
| `--raw --s 0` | the realism formula (also = "ugly") | — | 🟢 |
| `--c` / `--chaos` | variety across the 4-image grid | 0–100, default **0** | 🟢 concept / 🟡 values |
| `--weird` / `--w` | novelty / strange-style discovery | 0–3000, default **0** | 🟡 |
| `--seed` | repeatable blueprint — for **testing**, not consistency | 0–~4.29B, random | 🟢 concept / 🟡 mechanics |
| `--no` | exclude a thing (weight ~1, unreliable) | word | 🟢 |
| `::` | multi-prompt weighting; sum must stay **positive** | any number, neg ok | 🟢 |
| `--sw` | style-reference strength | 0–1000, default **100** | 🟡 |
| `--cw` | character-ref strength (0 = face only) — **weak lever** | 0–100, default **100** | 🟡 |
| `--iw` | image-prompt strength | 0–3, default **1** | 🟡 |
| `--ow` | omni-reference strength (v7) | 1–1000, default **100** | 🟡 |
| `--ar` | aspect ratio — **try many** | `w:h`, default **1:1** | 🟢 concept / 🟡 availability |
| `--draft` | ~1/4-cost fast exploration (v7); 1st gen only | flag | 🟡 |
| `--q` / `--quality` | detail vs. speed/cost | 0.25–2(–4), default **1** | 🟡 |
| `--hd` | higher-res alt algorithm | flag | 🟡 |
| `--exp` | experimental detail/variety (v7) — keep it low | low values | 🟡 |
| `--repeat` | run the prompt N times | up to ~34, use 5–10 | 🟡 |
| `{ }` | permutations — multi-prompt testing | caps ⚠️ unverified | 🟢 syntax / 🟡 limits |
| `--v` / `--niji` | model / version | — | 🟡 |
| `--tile` | seamless pattern | flag | 🟢 concept |
| `--stop` | halt at a % (softer look) | 10–100 | 🟡 |

---

## The three rules to actually remember

1. **Seeds give repeatability, not consistency.** Use them to isolate one variable (lock seed + `{,word}` + re-enter the prompt, don't reroll). For real consistency, use references.
2. **Don't anchor on one aspect ratio.** When a result is off, change `--ar` first — and run the same prompt across several ratios.
3. **Beauty and accuracy trade off.** `--s` high = pretty but loose; `--raw --s 0` = literal and real (and sometimes ugly). Move them deliberately, one at a time.
