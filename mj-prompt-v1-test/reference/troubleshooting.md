# Troubleshooting — making MJ listen

*When a prompt "isn't working" — MJ ignores a detail, a color, an angle, or just makes something prettier than what you asked for. This is the fix-it playbook.*

**Vintage:** distilled from a Midjourney creator's note vault + the v7-era course (~2025–2026). Tags: `mj-troubleshooting`, `mj-prompting`.

**Freshness legend:** 🟢 **Durable** — a principle that rarely changes; state it plainly. 🟡 **Volatile** — a UI location, default value, range, or version-specific behavior; **changes often, verify before asserting.** Hesitancy is targeted: don't hedge a 🟢, do hedge a 🟡.

---

## The one thing to internalize first

🟢 **MJ doesn't give you what you ask for — it gives you what *it* thinks you want, plus its own flair.** MJ is biased toward *beauty* and will quietly sacrifice your details to get there. Almost all "make it listen" tactics are about turning that bias **down** so your words come through.

🟢 **There is no silver bullet.** Several techniques below help; none is guaranteed. Sometimes you stack two or three. And sometimes (see [Hard limits](#hard-limits-what-mj-simply-cant-do)) MJ genuinely *can't* make the thing — don't burn 20 minutes rewording.

---

## The "make MJ listen" ladder

Work down this list in order. The early moves fix most problems on their own; reach for the later, heavier moves only when the cheap ones fail.

### 1. Lower stylize (`--s`) — *try this first*
🟢 Stylize controls how hard MJ chases its own idea of beauty. Lower stylize = MJ obeys *your words* more closely. **This alone often fixes it.**
- 🟡 Default `--s 100`, range `0–1000`. For accuracy, drop to **~40–60** (some notes go to `--s 30`). You *can* go to `0`, but expect ugly/unflattering results unless your prompt is very detailed.
- Syntax: `--s 40` or `--stylize 40` (space before the number). 🟢 Parameters always go at the **end** of the prompt; order among them doesn't matter.
- 🟢 Tradeoff to accept: more beauty = less accuracy. You're deliberately trading prettiness for control.

### 2. Add style raw (`--style raw`)
🟢 A "less opinionated," more literal sibling of the main model. Normally MJ silently pads short prompts with extra words to make them beautiful (a bare "dog" still looks gorgeous); raw strips most of that. Two effects: **(1) follows your prompt more closely, (2) favors realism.**
- 🟢 The realism formula: **`--style raw --s 0`** (raw favors reality, stylize 0 kills the artistic instinct). Warning: this is *also* the recipe for "ugly."
- 🟢 Effect is especially obvious in **Niji** (where the default is anime — raw pulls it back).
- ⚠️ Raw can mutate subjects when pushed (a documented case turned a girl into a shark). Use as a lever, not a default.
- 🟢 Escalation: lower `--s` **first**, then add `--style raw`, then combine both.

### 3. Rewrite the prompt as instructions ("drying off")
🟢 Once you've picked your words and it still won't render, **rewrite the description as separate, literal instruction-statements** that call back to the subject. Instead of cramming clauses, split them:
> ❌ "a robot in a white hooded jacket with two front pockets and green inside lining"
> ✅ "a robot in a white jacket. The jacket has a hood. The jacket has two front pockets. The jacket has green lining inside."

- 🟢 **Never use pronouns** (he/she/it). Always repeat the proper noun — "the robot… the jacket… the wizard…". Pronouns confuse the bot, and the longer the prompt the more this matters.
- 🟢 Positional words (left / middle / right / foreground / background) *do* carry meaning; "the first / the second…" does **not**.
- 🟢 Not a silver bullet, but the standard first move for a single stubborn detail.

### 4. Rearrange the words / flip subject ↔ setting
🟢 **Word order = emphasis. The first thing written is weighted most.** If a result is off, reorder before you do anything fancier.
- 🟢 "a person walking in a city park" centers the person, close to camera. "a city park with a person walking" widens the shot and pushes the person back. Same words, different image.
- 🟢 **Move an ignored word to the FRONT.** A documented case: "he is happy" did nothing at the end of the prompt, but worked when moved near the front. MJ also **ignores a lot of words near the end of a long prompt** — put the important ones early.
- 🟢 Write the concept **several ways** (usually ~3, up to 5) — e.g. for "fireworks shaped like an eagle," try "fireworks in the shape of an eagle" / "an eagle made of fireworks" / "an eagle in fireworks." Importance-ordering decides which reading wins.

### 5. Try a different aspect ratio — *cheap, underrated, try it early*
🟢 Changing the frame can transform a generation. **If results are off, one of the first things to change is the aspect ratio** (`--ar`).
- 🟢 Match the subject to the space (a car → wide `16:9`; a standing figure → tall `2:3`) — but **also just try random ratios.**
- 🟡 Ratios are relative (`10:5` = `2:1`); you can also type pixel dimensions directly (e.g. `1200x780`).
- 🟢 Related move: **generate square (`1:1`) first** (square tends to get the most accurate style), then **expand to your target ratio in the editor** rather than fighting the wide frame from the start.

### 6. Force a color — hyphenate to `-colored`
🟢 When MJ ignores a color, connect it to the word **"colored"** with a hyphen: `cyan-colored sportscar`, `coquelicot-colored suit`. This is the standard fix for a color that won't land.
- Related: for color *bleed* / too many colors, lower stylize + raw (step 1–2), or isolate the color as its own instruction ("the jacket is red").

### 7. Negative prompt (`--no`) and weighted "spice"
🟡 `--no <thing>` excludes something (`--no blur`, `--no camera`, `--no flowers`). Useful for a wrong-focal-length blurry full-body shot (`--no blur`) or a subject staring into the lens (`--no camera`).
- 🟢 Test it honestly: run **with and without** (a leading-comma permutation does this cleanly — see step 11). Some `--no` claims are placebo; verify on *your* prompt.
- 🟡 Multi-prompt "accents" — add extra emphasis as weighted fragments at ~**0.4–0.6** (raise/lower to change intensity). Multi-prompting with `::` splits the prompt into weighted fractions instead of reading it as one whole (more in the prompting/parameters references).

### 8. Add chaos (`--c`) to find a diamond in the rough
🟢 Chaos increases how *different* the 4 grid images are from each other. The fix when the grid is too samey — and a way to stumble onto a version that finally nails your detail.
- 🟡 Try **4, 8, 12**; try with and without `--style raw`; also try back at `--s 100`. Light, frequent values (3–5) are the everyday touch; 50–100 gets wild. The in-app slider jumps in steps of 5 (often too coarse) — type the value.

### 9. Image-prompt what you want (+ `/describe`, + image weight)
🟢 When words fail, **show MJ a picture.** Find a reference on Google, or build a rough concept in Canva/Photoshop in ~2 minutes, and feed it as an image prompt.
- 🟢 To **faithfully recreate** a reference: run `/describe` on it to get prompt words, then **crank image weight** (`--iw 2` or `--iw 3`), add `--style raw`, and lower stylize. A style reference (`--sref`) is another option.
- 🟢 To follow a rough concept **loosely**, keep `--iw` **low (~0.5)** so MJ doesn't just clone it.
- 🟡 `--iw` default is **1**; range **0–3** (v6/v7 — the v5 era was 0.5–2). Below 1 your text drives; at **2–3** it largely ignores your text and recreates the picture.
- 🟢 The minimal workflow that "generates any picture": **reference → `/describe` → review the suggested prompts → use the reference itself as an image prompt.**

### 10. Reroll, then vary
🟢 Treat the first grid as rough drafts — **99% of your images should be first drafts.** Don't abandon a near-miss; iterate it.
- 🟢 **Reroll discipline:** if a prompt fails, reroll up to **~3 times**; if it's still wrong after 3, *change the prompt* (don't keep rolling the same dice).
- 🟢 **Fix small defects with Variations (Remix OFF):** a minor flaw often disappears across the 4 new variations. Toggle remix quickly with `/remix`.

### 11. Confirm what a word is actually doing (lock a seed)
🟢 Before you trust *any* fix, prove it. **Lock a seed and change exactly one thing.** Any difference you see was caused by that change.
- 🟢 Cleanest A/B test: a **leading-comma permutation** runs the prompt with and without a word: `your prompt {,photogram} --seed 380382`.
- 🟢 Keep tests **narrow** — seeds give *repeatability*, not consistency (see myths). A small attribute/color change reads clean; a big swap (lion → walrus) breaks the comparison.

---

## Fixing a blurry image

🟢 The canonical anti-blur sequence (credited to creator "Henry Taylor"):
1. **Get out of draft mode.** Draft trades quality for speed/cost — a common, silent source of softness.
2. **Raise quality** (`--q`, e.g. `--q 4`) if it's a render-time issue.
3. **Prompt against it** — prefix with **"A detailed illustration..."** (his exact phrasing: *"A detailed illustration with spot color and gradient color fills of..."*).
- 🟡 Also: `--no blur` helps a blurry/wrong-focal-length full-body shot.

🟢 **Counterpoint — "why are my pictures so *sharp*?"** MJ tends to **over-sharpen on purpose**: a too-sharp image is easy to soften in Photoshop, but most users can't rescue a blurry one — so sharp is the safer default. If an image is *too* crisp, apply a light blur in post (a 0.7 Gaussian blur is the cited fix), don't fight the model.

---

## Accuracy: concepts vs. details

🟢 MJ is reliably good at **concepts** and unreliable at **specific details**:
- **Concepts / archetypes / scenes** — strong. Evocative words ("angelic cat," "warrior," "gentleman") and whole scenes come out well.
- **Specific details** — weak by default. A word obvious to *you* isn't obvious to the bot. **The one limitation you can directly control is specificity** — layer on more descriptive language ("a cat on a windowsill" → "a cat on a windowsill, the cat is wearing a suit and tie, the cat is wearing a hat").

🟢 **Motion is a detail it struggles with** ("running," "jumping" are hard to draw and under-represented in training data). **Fix: shrink the moment to a stationary instant.** Instead of "a boy running through a field" (5–10 seconds of implied time), prompt "a boy high up in the air" or "a boy in a superhero landing." Capture a fraction of a second, not an action.

🟢 **Faces/hands were weak in older versions** (🟡 much improved since) — the fix was iteration: a grid gives one image with a good nose, click in; find one with good nose + ears, click in again, repeat.

🟢 **Why details are hard — it cuts both ways:** sometimes *too little* data (an obscure animal, a minor TV character → the bot has no idea), sometimes *too much variety* (hands appear in nearly every photo but in endless positions, so there's no single "correct" hand to converge on).

---

## Hard limits — what MJ simply can't do

🟢 **The bot can't render what wasn't in its training data, and no prompt fixes that.**
- It knows "Nike shoe," **not** "Nike Air Pegasus from 2005." For **ultra-specific real-world items**, drop the exact name and describe it instead ("stylish sneakers").
- This bites hardest on **specific people/objects** (more than whole scenes). If MJ wasn't trained on your favorite show, it won't reproduce that character accurately — **don't waste 20 minutes rewording.**
- 🟢 **IP can hijack a prompt.** A strong existing property overrides you (the *Detective Pikachu* movie kept hijacking "Pikachu"). Fix by adding disambiguating qualifiers: "pikachu **as an ugly puppet from a 1980s movie**." Obscure characters may need it too ("Tien **from Dragon Ball Z**").

---

## Myth-busting — things that do NOT work

The creator is emphatic about bad advice that circulates on YouTube. Don't waste effort on these:

🟢 **Reactions don't teach MJ.** Hearting/emoji-reacting to an image does **nothing** to make future generations better or more consistent — *MJ doesn't learn from reactions.*
> Reconciled nuance: emoji reactions in the Discord bot *are* functional **commands** (✉️ DMs you the seed/job-id, ⭐ favorites, ❌ deletes). They do real things — they just don't **train the model on your taste.**

🟢 **"octane render" / "unreal engine" don't create consistency.** Adding render-engine words does **not** make characters consistent across images. (Those words read as "make it photorealistic," nothing more.)

🟢 **Stacking quality words adds nothing.** "detailed, highly detailed, ultra detailed, hyper detailed" → just say **"highly detailed."** "4k, 8k, 16k" don't stack — *"you're not going to get 28k out of it."* Redundancy isn't harmful, but it's a bad habit: it hides what each word is actually doing.

🟢 **Seeds are *repeatability*, not consistency.** Same prompt + same seed ≈ the same image (~99.5%). But seeds are **not** a character-consistency tool — *any* change to the prompt accesses a brand-new blueprint (out of ~4 billion). Use a seed to **reduce variables while testing**, not to keep a character. Seeds affect **composition** more than fine details; locking one narrows your composition (often not what you want). (For real consistency use `--sref`, mood boards / `--p`, or `--cref`/omni-ref — see the consistency reference.)

🟢 **MJ has no memory and doesn't learn from you.** It generates fresh from random seeds every time.
> Reconciled contradiction: a popular trick claims you can image-prompt a character + type its name to "teach" MJ the identity. The creator **tested this directly** (Officer Jenny from Pokémon) and it **did not work** — so the default verdict is *busted*. One community anecdote (the "Alice Cooper" story) reported an image prompt *did* nudge later generations toward the right identity. Treat that as a rare, unreliable edge case, not a method — MJ has no persistent memory; at most a *within-session* image prompt is biasing the current job.

🟢 **Remix doesn't relocate a character into a new scene.** It mostly changes colors and behaves more like *replacing* a subject (composition stays too similar). **Image-prompting a multi-panel character sheet just reproduces those same panels/poses** — it can't re-pose your person.

🟡 **Some `--no` / phrasing tricks are placebo.** e.g. `--no talking, speaking, moving lips` for video is unproven (one tester says it does nothing). Always A/B with a locked seed before believing a fix.

---

## Quick reference card

| Symptom | First move(s) |
|---|---|
| MJ ignores my details / too "pretty" | Lower `--s` (40–60) → add `--style raw` |
| One stubborn detail | "Dry off" — rewrite as literal instruction-statements, no pronouns |
| A color won't land | Hyphenate: `red-colored …` |
| Wrong composition / framing | Reorder words (important first); flip subject↔setting; **try a new `--ar`** |
| Grid all looks the same | `--c 4/8/12` |
| Blurry | Leave draft → raise `--q` → prefix "A detailed illustration…" |
| Too sharp | Light Gaussian blur in post (~0.7), don't fight the model |
| Can't get a specific real item | Describe it generically; it may simply not be trained in |
| Existing IP hijacks the prompt | Add qualifiers ("as an ugly puppet from a 1980s movie") |
| Motion looks wrong | Shrink to a stationary instant (mid-air, not "running") |
| Need to recreate a reference | `/describe` → image-prompt with `--iw 2/3` + raw + low `--s` |
| Want to verify a fix actually worked | Lock a seed, change one thing (leading-comma permutation) |
| Nothing works after ~3 rerolls | Change the prompt — or accept MJ can't make it |

---

*Cross-references (if the full skill is installed): prompting fundamentals (word order, instructional prompting, callbacks), parameters (`--s --raw --c --ar --seed --iw --no`), consistency (`--sref`, mood boards, `--cref`/omni-ref), testing (seeds + permutations).*
