# Template: Viral Hook Image — Real Person

**Use when:** generating the cover/hook image of an Instagram carousel, TikTok, or Reel
where the payoff is "this is a real human talking to me." The person in the image should
read as authentic — like a real creator pulled a photo from their camera roll — not like
an AI-generated headshot.

## Critical prerequisite: read `reference/camera-roll-energy.md` first

The biggest trap for viral hook images is **photographer energy**: golden hour
sidelight + shallow depth of field + centered composition + subject facing camera
+ styled outfit. Even with perfect photorealism tokens, this composition makes
the output look "staged AI image."

**For viral social content, push every slider toward camera-roll energy:**
- Flat overcast light (NOT golden hour)
- Everything mostly in focus (NOT shallow DoF / bokeh)
- Off-center, slightly tilted framing (NOT centered)
- Subject looking at phone / off-frame (NOT facing camera)
- Cluttered background with real street mess (NOT clean / minimalist)
- Wrinkled, basic clothes (NOT styled outfit)

The template below bakes this in. **Do not remove these signals** unless you
specifically want editorial energy (e.g. About Page portraits — use
`lifestyle-portrait.md` for those).

## Rule #1 — No text in the generation

Overlay the hook text separately (Canva, Figma, CSS, sharp). Nano Banana WILL garble it.
The prompt should explicitly say: `no text, no captions, no writing, no watermark`.

---

## The template (camera-roll energy — USE THIS)

Fill the `{BRACKETED}` slots. This longer-than-usual template explicitly bakes
in all 7 camera-roll moves. Do not strip for length — each signal matters.

```
Random iPhone snapshot of {SUBJECT — age + wrinkled/basic clothing + imperfection},
{CANDID ACTION — not facing camera, e.g. "looking down at phone"}, {SLIGHT SLOUCH
OR HUMAN DETAIL}, not facing the camera.

{BACKGROUND CLUTTER — name 2-3 messy elements: pedestrians, bus, trash bin, etc.}

Flat overcast {TIME} light, no golden hour, no rim light, even dull diffusion.

Shot on iPhone 13, rear camera, handheld shaky framing slightly tilted,
visible JPEG compression artifacts, slight motion blur, slight noise in shadows,
visible skin pores, {IMPERFECTION: uneven stubble / under-eye shadows / etc.},
faint asymmetry in face.

Off-center composition with subject in {left|right} half. 9:16 aspect ratio.
No text, no captions, no readable signs.

Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
symmetrical face, HDR glow, AI aesthetic, stock photo feel, supermodel look,
male model look, professional photograph, magazine cover, centered composition,
golden hour, bokeh background, shallow depth of field, styled outfit, posed,
photoshoot energy.
```

**Word count:** ~100 words. That's intentional — the anti-photographer signals
need to overpower the model's default bias.

---

## Worked example (the one that worked on the user's "too AI" test)

**User concept:** "normal person, not too prepared, phone-taken picture feel"

**Filled template:**

```
Random iPhone snapshot of a 28-year-old man in a slightly wrinkled grey hoodie
and faded black jeans, mid-stride on a crowded Barcelona sidewalk, looking down
at his phone in one hand, slight slouch, other hand holding a takeaway coffee
cup, not facing the camera.

Other pedestrians slightly visible in the background, some out of focus, a bus
passing behind, a trash bin on the left edge of frame.

Flat overcast midday light, no golden hour, no rim light, even dull diffusion.

Shot on iPhone 13, rear camera, handheld shaky framing slightly tilted, visible
JPEG compression artifacts, slight motion blur on hand and phone, slight noise
in shadows, visible skin pores, uneven stubble with patchy growth, slight
under-eye shadow, faint asymmetry in face.

Off-center composition with subject in right half. 9:16 aspect ratio. No text,
no captions, no readable signs.

Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed, symmetrical
face, HDR glow, AI aesthetic, stock photo feel, supermodel look, male model look,
professional photograph, magazine cover, centered composition, golden hour, bokeh
background, shallow depth of field, styled outfit, posed, photoshoot energy.
```

**Why this works — the camera-roll signals doing the work:**

| Signal | Token that fires it |
|---|---|
| Not facing camera | "looking down at his phone in one hand, not facing the camera" |
| Background clutter | "pedestrians... a bus passing behind, a trash bin on left edge" |
| Flat / non-dramatic light | "flat overcast midday light, no golden hour, no rim light" |
| Amateur framing | "handheld shaky framing slightly tilted, off-center" |
| Lived-in clothes | "slightly wrinkled grey hoodie, faded black jeans" |
| Compression authenticity | "visible JPEG compression artifacts, slight noise in shadows" |
| Human imperfection | "uneven stubble with patchy growth, slight under-eye shadow" |
| Expanded anti-photographer negatives | "golden hour, bokeh, shallow DoF, centered, posed, photoshoot energy" |

**Result:** viewer reads "a friend took a pic of this guy walking" — not
"this was posed for a photographer." That's the signal that unlocks viral feel.

### Alternative (ski slope variant, matches user's original reference)

```
Random iPhone snapshot of a 24-year-old man in a brown puffer jacket and white
beanie, standing on a snowy mountain terrace looking off-frame at the view,
not facing camera, one hand holding ski poles loosely, slight slouch. Other
skiers visible in the background, a ski lift pylon on the right edge of frame,
cable blurred by movement. Flat overcast alpine light, no golden hour, no rim
light, even dull diffusion. Shot on iPhone 13, rear camera, handheld slightly
tilted, visible JPEG compression artifacts, slight motion blur, slight noise
in shadows, visible skin pores, uneven stubble with patchy growth, faint
asymmetry in face. Off-center composition with subject in right half.
9:16 aspect ratio. No text, no captions, no readable signs.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed, symmetrical
face, HDR glow, AI aesthetic, stock photo feel, supermodel look, male model
look, magazine cover, centered composition, golden hour, bokeh, shallow depth
of field, styled outfit, posed, photoshoot energy.
```

---

## Variations by niche

### Fitness creator
```
Candid iPhone photo of a 27-year-old woman in a sweat-stained grey tank top and
black leggings, kneeling on a rubber gym floor with a loaded barbell behind her,
tired expression, damp hair, hand wiping forehead. Harsh gym overhead light,
slight fluorescent flicker, shadow under chin. Shot on iPhone 15 Pro, rear camera,
slight motion blur, visible skin pores, peach fuzz, cinematic catchlight in eyes,
slight asymmetry in face. 9:16 aspect ratio. No text, no captions.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed, AI aesthetic,
fitness model look, stock photo feel.
```

### Founder / SaaS
```
Candid iPhone photo of a 31-year-old man in a wrinkled grey t-shirt and unshaven
jaw, sitting in front of a cluttered desk with two monitors showing code and
a half-empty coffee cup, looking slightly tired into the camera. Afternoon window
light from the left, natural shadow on right side of face. Shot on iPhone 15 Pro,
rear camera, slight grain, visible skin pores, peach fuzz, cinematic catchlight in
eyes, slight asymmetry. 9:16 aspect ratio. No text, no captions.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed, symmetrical face,
HDR glow, AI aesthetic, LinkedIn headshot polish.
```

### Travel / lifestyle
```
Candid iPhone photo of a 26-year-old woman in a linen shirt and light jeans,
sitting on the edge of a sun-bleached stone wall in a narrow Mediterranean alley,
olive trees behind her, scuffed sneakers, holding a folded paper map. Late afternoon
sidelight, warm golden tones, long shadow from her body. Shot on iPhone 15 Pro,
rear camera, slight vignette, visible skin pores, peach fuzz on cheek,
cinematic catchlight in eyes. 9:16 aspect ratio. No text, no captions.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed, HDR glow,
influencer look, AI aesthetic.
```

### Personal finance (like the user's ski example)
```
Candid iPhone photo of a 24-year-old man in a charcoal overcoat over a white
t-shirt, walking out of a revolving glass door of a Barcelona office building,
phone in one hand, slight tired half-smile. Cool overcast morning light, soft
shadow, no hard sun. Shot on iPhone 15 Pro, rear camera, slight motion blur,
visible skin pores, peach fuzz, cinematic catchlight in eyes, slight asymmetry.
9:16 aspect ratio. No text, no captions.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed, symmetrical face,
HDR glow, AI aesthetic, model look, stock photo feel.
```

---

## After generation — the text overlay step

Once Nano Banana returns the clean photo, overlay text with one of:

### Option A — Canva (manual, fastest)
1. Upload the photo.
2. Pick a bold condensed sans-serif (Impact, Bebas Neue, Oswald).
3. Color: white with a soft drop shadow (not a hard black outline — dated).
4. Hook line goes in the top third. Keep it to 2 lines, readable at thumbnail size.

### Option B — `sharp` + SVG (programmatic, for autoposter pipelines)
```js
const sharp = require('sharp');
const svgOverlay = `
<svg width="1080" height="1920">
  <style>
    .hook { font: 900 72px 'Arial Narrow', sans-serif; fill: white;
            text-anchor: middle; }
  </style>
  <text x="540" y="300" class="hook">HOW TO START INVESTING</text>
  <text x="540" y="380" class="hook">STEP BY STEP</text>
</svg>`;

await sharp('generated.jpg')
  .composite([{ input: Buffer.from(svgOverlay) }])
  .toFile('final.jpg');
```

### Option C — HTML → canvas → image (for full creative control)
Render an HTML template with the photo as background and the text as styled DOM,
then screenshot with Puppeteer at 1080×1920. This gives full typography control,
handles curved layouts, and matches exactly what viral posts look like.

---

## Failure mode quick-reference

| Result looks... | Fix in the prompt |
|---|---|
| Like a model / too attractive | Add specific imperfection, remove any positive adjective |
| Like a stock photo | Name a real place, add 1 scene prop, drop polished setting |
| Like an AI face | Re-check: did you include `iPhone 15 Pro, rear camera`? Did you include catchlight + pores? |
| Like a LinkedIn headshot | Remove "professional," add "candid," "slight motion blur" |
| Creepy / uncanny | Usually eyes — add `natural specular reflection in iris`, `slight asymmetry` |
| Text got mangled | You forgot — remove all text from prompt, overlay in post |

---

## Why this template works (the theory)

Nano Banana's training data is heavily biased toward:
- Retouched editorial / fashion photography
- Stock photo libraries
- Over-polished Instagram influencer content

Left to defaults, it regresses to the statistical mean of that data, which is
"AI slop aesthetic." To break out, you need **specific counter-signals** at every layer:

- Camera hardware references trigger a different distribution of training data
  (phone snapshots, not studio)
- Texture tokens force the model to render light-skin interactions at micro-level
  (it knows what pores look like, it just needs permission to draw them)
- Negative constraints block the regression to AI aesthetic
- Specific locations + imperfect subjects ground the output in reality

Skip any of these and the model drifts back to AI slop. That's the second screenshot
the user showed: no camera token, no texture tokens, generic subject → pure AI face.
