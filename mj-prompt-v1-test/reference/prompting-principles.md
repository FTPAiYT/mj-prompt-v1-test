# Prompting Principles & Structure

How to *build* a Midjourney prompt. This is the conceptual craft layer — word order, scene-building, the recipes, the mental models — distilled from a working creator's note vault. Parameter mechanics (`--s`, `--c`, sref/personalization codes) live in sibling files; this file is about the **words**.

**Legend:** 🟢 durable principle (model-agnostic; survives version changes) · 🟡 volatile (version- or UI-specific; confirm against current MJ).

> **The one-line philosophy:** *Treat Midjourney like an artist you hired, not a search engine you're querying.* It will always add its own flair and never give you exactly what you asked for — that 1% it sways is the point. You guide; it interprets. So you're not writing rules, you're giving creative direction.

---

## 1. The core build order

🟢 **Start with subject + setting.** Establishing a scene (background/environment) is the single highest-impact thing you can do — and the most commonly missing piece in a weak prompt. A bare subject ("a spaceship") falls back to MJ's defaults (a generic nebula); name the setting ("a spaceship, in a swirling nebula at dawn") and you take control.

🟢 **Word order = emphasis. The first words are weighted most heavily.** Whatever you write first reads as the main subject; leading with the setting pushes the subject smaller and farther away. This isn't subtle — it's a "big difference."
- `a medieval knight walking in a busy mall` → knight is the hero, close up.
- `a busy mall with a medieval knight` → wide shot, knight is incidental.
- If you don't like a result, **swap subject and setting** before anything else.

🟢 **The triangle:** the three things you're always balancing are **style / subject / background**, and whichever you put **first** dominates. Setting can accent the character, or the character can accent the setting — you decide by what leads.

---

## 2. Two ways to prompt (and a third)

🟢 **Open-ended / "vibe" prompting** — lean on the bot's knowledge. Give it an evocative subject and let it fill in: *a cool koala*, *the perfect dessert*, *a triumphant octopus*, *a forgotten technology*, *a gorilla in a fancy suit but disappointed*. You trade fine control for speed and surprise. Best for exploration and when you don't know what you want. *Implying* what you want often works when stating it fails.

🟢 **Instructional / explicit prompting** — when you have a specific vision, write it as clear instructions (see §3). You trade some magic for control.

🟢 **Poetry / abstract prompting** — full lyrical phrasing works too: *"my love shines with the strength of a star in your darkened eyes"*, *"knowledge and terror hold hands under the table."* Strong feelings and mystical themes land especially well — awe, nostalgia, dread, wonder, *the shores of infinity*, *the birth of time*. Use it for mood.

🟢 **Dry vs poetic both work.** "A cat eating a pie" and a poem about cats both parse. The register you choose just controls how much you're letting MJ fill in versus pinning down. Pick whichever fits the job; don't assume you must sound "promptish."

---

## 3. Instructional prompting — the rules

When you want control, write the prompt like directions to a collaborator:

🟢 **Open with a scene-setting "opening statement."** State the whole scene in one line: *"a cat on a windowsill."*

🟢 **Add each detail as its own statement that calls back to the subject.** *"the cat is wearing a suit and tie. the cat has a red bandana."* Repetition of the noun is the link that tells the bot what each clause modifies — and it's described as *the most powerful prompting technique*:
- Weaker: `a large blue building surrounded by green palm trees`
- Stronger: `a large building. the building is painted blue. the building is surrounded by green palm trees.`

🟢 **NEVER use pronouns** (he / she / it / they). Always repeat the proper noun: *"the man… the man… the wizard…"*. Pronouns make the bot lose the thread, especially in long prompts. With two characters, name both every time (or give them a shared action).

🟢 **State positions before actions.** Don't write *"the kangaroo jumps over the man."* Write *"there is a kangaroo on the left and a man on the right. the kangaroo jumps over the man."* Positional words — left / right / center / foreground / background / "far in the distance" — carry real weight; lay the spatial groundwork first.

🟢 **The longer the prompt, the more all of this matters.** More words = more room for error. Which is exactly why you start small.

---

## 4. Start small, then elaborate

🟢 **Begin with a simple core, then add one element at a time.** You can watch what each word does, and it's far **easier to add a missing word than to subtract a noisy one.**
- `man in a kaftan` → `man in an armored kaftan` → `man in an armored dieselpunk kaftan` → `hindu man in an armored dieselpunk kaftan`.

🟢 **First generations are rough drafts.** A grid of 4 is four first drafts — you're hunting for ~1 in 4 that blows you away, not four keepers. If two grids in a row are bad, *it's probably your prompt's fault.* Look at where the bot fell short and insert that expectation as a new statement.

🟢 **"Just elaborate" is the whole skill.** Mastery is incremental description — add a detail, describe the mood, focus on the atmosphere — not memorizing jargon. Build like Lego: one piece at a time, evaluate, add the next.

---

## 5. Snapshots, not scenes

🟢 **Prompt a 1–2 second moment, not a 10-second scene.** MJ freezes a single instant; it can't show a sequence. *"a woman walking down the street and then getting into a car"* is two events — it will fail. Reduce to one freeze-frame:
- ✗ "a boy running through a field" (implies time) → ✓ "a boy mid-leap, high in the air."
- Think like a photographer catching one shutter-click, not a director shooting a take.

---

## 6. "Drying off" a stubborn prompt

🟢 When a detail won't render, **rewrite that description as separate, matter-of-fact statements** instead of cramming it into one phrase. Break the parsing jam into distinct assertions:
- ✗ `a robot in a white hooded jacket with two front pockets and green inside lining`
- ✓ `a robot in a white jacket. the jacket has a hood. the jacket has two front pockets. the jacket has green lining inside.`

🟢 Likewise, converting commas → periods and writing in plain prose often helps **your own brain** design a cleaner prompt, even when it barely changes the output.

🟢 Not a silver bullet — but it's the first move for a detail that keeps getting ignored.

---

## 7. No true negatives

🟢 **Mentioning a thing summons it.** MJ reads any noun you write as *wanted*. `a dress without wrinkles` keeps the wrinkles; `the person has no rings` weights "rings." The fix is to **prompt the inverse — describe what you DO want:**
- ✗ "a dress without wrinkles" → ✓ "a firm, clean, ironed dress."
- ✗ "the person has no rings" → ✓ "the person has clean hands."

🟡 The `--no` parameter *does* work for cleanup (e.g. `--no camera`, `--no mockup`, `--no text`) and even doubles as an aesthetic lever (`--no red` can shift a whole image's mood) — but never negate inside the prose itself.

---

## 8. Concept vs specific (and the bot's associations)

🟢 **You're learning the BOT's associations, not dictionary definitions.** This is the single most important framing. A word is a lever for what the model learned from training data — not what the word "means." A poetic word that moves you may do nothing; a plain one may transform everything. The only way to know is to test it (lock a seed, run the prompt with and without the word — if the grid looks the same, the word does nothing).

🟢 **The bot knows categories, not rare specifics.** It knows "Nike shoe," not "Nike Air Pegasus from 2005." It can't render what wasn't in its training (obscure characters, a platypus took ages to learn). **There is no silver bullet** — sometimes it simply can't make what you ask. The workaround: **describe with concepts** ("stylish sneakers," "a Saiyan warrior" instead of "a Goku").

🟢 **Multi-phrasing.** If a concept keeps slipping, write it 2–3 different ways (up to ~5) so the bot catches it from multiple angles: *"fireworks in the shape of an eagle, an eagle made of fireworks, a firework display forming an eagle."*

---

## 9. Adjectives are the "how"

🟢 **Adjectives of degree and manner are more powerful than object names** — they direct the *how*, not just the *what*. "a gigantic phone" vs "a miniature phone" reshapes the whole scene.

🟢 **Verbs/actions beat flat adjectives for attitude.** "cool koala" (an appearance) vs **"koala being cool"** (a behavior) — the second makes the koala *act*. Same with poses: "spinning, arms outstretched" reads with motion that "arms outstretched" lacks.

🟢 **For poses and expression, describe the feeling, not just the anatomy.** Three ways to get a pose: (1) literally describe the body, (2) describe the emotion the pose should evoke, (3) **combine a short physical cue + the emotion** — the creator's favorite, *"works best"*: "standing in a powerful pose, looking confident." Facial expression and weather are the two most-forgotten high-impact details.

---

## 10. Archetypes

🟢 **Archetypes are strong scaffolding** — the bot has rich pre-learned associations. "a female angelic knight," "a wizard," "a warrior," "owner and pet" snap into place without much detail. Use them when you want reliability fast.

🟢 **But archetypes resist off-type traits — coin a new noun to escape.** The bot fights details that don't fit the archetype:
- "a cat with purple hair" fights you (cats don't have purple hair) → coin a non-cat noun like **"a filinoid"** (modeled on "humanoid") to free it. (Spelling is approximate — the point is to change the *archetype*, not to nail a specific word.)
- For a green-skinned woman, "woman with green skin" fights the human archetype → "a female humanoid bodybuilder" changes the archetype itself.
- Heads-up: **"model"** raises the odds your subject stares into the camera (models pose). Swap the noun if you want no eye contact.

---

## 11. Style vs aesthetic vs medium

🟢 You build a look from word categories. The exact label doesn't matter — **awareness of the levers does.**
- **Style = how it looks** — watercolor, chibi, pixel art, caricature, de stijl, cubism.
- **Aesthetic = how it feels** (the vibe) — cottagecore, film noir, cyberpunk, vaporwave, gothic, medieval.
- **Medium = how it's made** — oil painting, origami, beadwork, collage, stained glass, charcoal.

🟢 **Styles combine** — "chibi watercolor sportscar" ≈ a 50/50 blend. Mixing categories is the best part of working with AI: "a cyberpunk scene (aesthetic) in watercolor (style) on canvas (medium)."

🟢 **Lead with the style/medium when you want it to dominate.** "Vogue portrait photoshoot of Walter White in a dirty RV" sets the visual register before the content. (Style references get picked up regardless of position, but front is a fine default.)

🟢 **Lean INTO a style's tendencies** rather than fighting them (e.g. M.C. Escher → give it impossible geometry to chew on).

---

## 12. Power prompts (power words)

🟢 **A power word is any single word that overpowers and transforms a whole generation** — it does "the work of entire paragraphs": *cybernetic, elegant, zentangle, deep dream, blacklight, anaglyph, low poly, surreal, cyborg, illuminated manuscript.*

🟢 **Clean structure for them:** **`[power prompt] style [subject]`** — e.g. "cybernetic style koala," "elegant penguin in an elegant setting." The power word usually goes early and anchors everything.

🟢 Mental model: *all art styles are power prompts, but not all power prompts are art styles.* Other reliable anchor words act the same way — "wallpaper" (polished full-frame), "candid" (unposed, fly-on-the-wall), "unsplash" / "stock photography" (clean photographic look), "made of ___" (spoons, beads, ferrofluid — a versatile transformer).

---

## 13. Color forcing

🟢 When MJ ignores a color, force it with one of these:
- **`[color]-colored`** — hyphenate the color to the word "colored": `cyan-colored sportscar`, `coquelicot-colored suit`.
- **"mostly [color]"** — designates the dominant color; pairs well with `--style raw`. `the phone is mostly yellow`.
- **"ombre"** — blends *between* colors (a gradient). `a blue / green / yellow ombre sweater`.
- **"monochrome [color]"** — "monochrome red" works; "monochrome" alone is ambiguous.

🟢 Hex codes and RGB do **not** work — plain language does. *tint / tone / shade / hue* are effectively synonyms; don't agonize over which.

🟢 For mood-driven color, **time-of-day words** ("golden hour," "dusk," "blue hour," "twilight") steer lighting and palette more reliably than abstract color-theory terms.

---

## 14. Composition & format recipes

🟢 Reach-for-these layouts (name the format explicitly):
- **Full-body trick** — to force a head-to-toe framing, *mention something on the head AND something on the feet* (e.g. a hat + boots, hair color + shoe color). This is far more reliable than meta-instructions like "full body shot," because it gives MJ content it must render at both ends. (Adjusting the aspect ratio taller helps too.)
- **Triptych / diptych / multi-panel** — "three-panel triptych," "horizontal diptych," "6 panels with different dynamic poses."
- **Character / sprite sheet** — "character sheet," "character design," "sprite sheet" in a **wide ratio** (16:9, 3:2) to pack multiple poses/angles into one image. "pixel art sprite sheet" is very reliable.
- **Knolling** — "knolling photography," neatly arranged objects top-down (great for "alien cuisine" / asset layouts). Pairs with a fish-eye lens.
- **Double exposure** — name both layers: "a double exposure, one layer a woman, the second a cityscape in watercolor." Combine with a medium like origami for extra effect.
- **Enclosed in a circle** — "centered in a circle," "mandala-style," diorama, origami framings.
- **2D + 3D pairing** — add "sculpture" or the word "3d" to a flat style (e.g. a cubist Batman *sculpture*; road chalk made 3d).
- **Going against the grain** — pick an *unexpected* aspect ratio for a subject (a vertical kung-fu still, a wide polaroid). Mismatching ratio to subject forces creative reframing.

🟢 **Camera/shot vocabulary controls framing:** low-angle (looking up), eye-level, aerial view (very reliable), over-the-shoulder, wide-angle (pulls back), fish-eye selfie. **Prefer "view" or "angle" over "shot"** — "candid shot" can drag a literal camera into frame; "candid view" / "candid angle" stays clean.

---

## 15. References overpower words — so wording still matters

🟢 Image generation has shifted toward visual references: a mood board, an image prompt, or a style reference will **overpower** your text. That's *why prompting still matters* — to coax a similar look without fighting the reference, and to direct the specifics *within* the reference's style. They work together; words and references aren't either/or.

🟢 **"Show, don't tell."** When a look is hard to describe, show it (mood board / image prompt) instead of piling on adjectives. But even then — **describe the board.** A mood board or omni-reference does much more when you also mention what's in it.

🟢 **Concept vs specific, restated:** for an exact thing, a reference image beats any wording; for a *vibe*, words and style refs together get you there.

---

## 16. Mental models worth keeping

🟢 **The chef and the pantry.** *"A cook has ingredients in their kitchen. I skim my mental pantry and pull out words I know I like that'll work well together."* A prompt is a recipe; each word is an ingredient; `::` is a dash of spice. Build a personal pantry of words you've seen work.

🟢 **Treat it like an artist.** You're giving creative direction to a collaborator with its own taste — not programming a machine. Give it a direction, a vibe, and a few anchors, then let it create. *"AI doesn't lower the ceiling, it just raises the floor."*

🟢 **Use it as a creativity spark.** When you have no idea, prompt loosely and let the grid suggest the idea. The most powerful everyday workflow: **find a picture you like → remix it into new subjects → build a mood board from those results.**

🟢 **Trust intuition over grand theory.** MJ has ~4 billion seeds; you will never see everything a prompt can do, and confirmation bias invents "rules" that aren't real. When a generation lands, **note its settings — those are now *your* godly parameters** — and move on. Iteration, not theory, is the path to the gold.

---

## 17. Format & syntax notes

🟢 **Commas blend; `::` splits.**
- `dog, van gogh, bob ross` → one unified concept (a dog rendered by both, blended).
- `dog::1 van gogh::1 bob ross::1` → three independent weighted parts (~33% each).
- Bonus: a split prompt frees the seed to the *first* term — `a corgi :: watercolor` and `a corgi :: ice sculpture` share the same base composition in different styles.

🟢 **Weights are relative, not absolute** — `dog::1 cat::8` makes the cat 8× stronger. Negative weights work (`neon::5 black and white::-1`), but the **sum must stay positive** or the prompt fails. A space before `::` is fine; a space *after* it breaks parsing.

🟢 **Hyphenation can matter** — "pop-art" may behave differently from "pop art." If a two-word term underperforms, try it hyphenated.

🟡 **Text in images:** put the words in quotation marks — `a koala that says "Congrats!"`. Short words work; long sentences fail; add lots of text in *batches* rather than one giant quote. Text handling improves every version — re-check current capability.

🟡 **Capitalization doesn't matter; spelling sometimes does** (a misspelled word can pull a different association — test with a locked seed). Any punctuation is fine; use whatever's easy to re-read later.

---

## 18. Quick reference — formula skeletons

Pick a skeleton, fill what you need, **drop the parts you don't.** None is mandatory; they're scaffolds for when you're stuck.

🟢 **Beginner four-part:** `Art style + Technique + Atmosphere + Adjectives`

🟢 **The full checklist (a "mental pantry" of categories to consider):**
`subject · setting · background · size/scale · mood · atmosphere · color · style · medium · camera/lens · material/texture · time period · culture · emotion · artist or photo source · shape/form · technique · aspect ratio`

🟢 **The 2-4-2 rhythm:** subject/setting — *detail · detail · detail · detail* — accents (atmosphere/weather/emotion). A loose cadence, not a rule; it rescues a flat prompt.

🟢 **Portrait recipe:** `(style) portrait of (subject), (1–2 features), (pose), (fashion), (background), (camera + lens)`

🟢 **Cinematic recipe:** lead with `cinematic still` → subject → director/genre suffix; add cinematic lighting, a camera + lens, a real photo source (`by Vogue`, `national geographic`). Directors and photo-source names work best **near the front.** *(Citing real photo sources beats inventing artist names for photographic quality.)*

🟢 **Photoreal recipe (concept-level):** `[subject], unsplash, candid, cinematic still, stock photography` — plus, mechanically, lower stylize + `--style raw`. (Detailed camera-spec stacks like `85mm, f/8, ISO 100` also read as "photographic" because the bot associates that jargon with real photos.)

🟢 **Sticker recipe:** `(subject), sticker, (mood), (color story), (art style), die-cut white border, isolated, no background, (detail level)`

---

*Sources: the creator's MJ course synthesis (prompting fundamentals, styles & words), the prompt-formulas tip grid, and ~26 batches of ingested working notes. Version-tagged specifics (text handling, `--no` behavior, MJ versions) are marked 🟡 — confirm against the current model, since "EVERYTHING is subject to change."*
