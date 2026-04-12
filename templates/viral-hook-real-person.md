# Template: Viral Hook Image — Real Person

**Use when:** generating the cover/hook image of an Instagram carousel, TikTok, or Reel
where the payoff is "this is a real human talking to me." The person in the image should
read as authentic — like a real creator pulled a photo from their camera roll — not like
an AI-generated headshot.

**This is the user's #1 use case.** The good screenshot they showed:
a guy on a snowy ski slope, winter jacket, slight smile, real phone photo energy,
with bold white text overlaid: *"HOW TO START INVESTING STEP BY STEP — from a 24 year old who built a 6-figure portfolio."*

## Rule #1 — No text in the generation

Overlay the hook text separately (Canva, Figma, CSS, sharp). Nano Banana WILL garble it.
The prompt should explicitly say: `no text, no captions, no writing, no watermark`.

---

## The template

Fill the `{BRACKETED}` slots. Keep total length 25–60 words.

```
Candid iPhone photo of {SUBJECT with 1 specific imperfection} in {GROUNDED LOCATION},
{LAYER 1 ACTION}. {LIGHTING: directional + time of day}.
Shot on iPhone 15 Pro, rear camera, slight motion blur, visible skin pores,
peach fuzz on jaw, cinematic catchlight in eyes, slight asymmetry in face.
9:16 aspect ratio. No text, no captions, no writing in the image.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed, symmetrical face,
HDR glow, AI aesthetic, stock photo feel.
```

---

## Worked example (finance creator, ski slope)

**User concept:** "guy on a ski slope talking about investing"

**Filled template:**

```
Candid iPhone photo of a 24-year-old man in a brown puffer jacket and white beanie,
standing on a snowy mountain terrace with ski lifts and fog in the background,
slight crooked smile, hands relaxed at sides. Overcast alpine light, soft diffusion,
no hard shadows. Shot on iPhone 15 Pro, rear camera, slight motion blur, visible
skin pores, peach fuzz on jaw, cinematic catchlight in eyes. 9:16 aspect ratio.
No text, no captions, no writing in the image.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed, symmetrical
face, HDR glow, AI aesthetic, stock photo feel, supermodel look.
```

**Why this works:**
- **"24-year-old"** → specific age, not "young man" (idealization trigger)
- **"brown puffer jacket and white beanie"** → lived-in clothes, not "stylish outfit"
- **"snowy mountain terrace with ski lifts and fog"** → grounded location, AI has anchors
- **"slight crooked smile"** → asymmetry, breaks doll-face default
- **"Overcast alpine light, soft diffusion"** → directional lighting Nano Banana understands
- **"iPhone 15 Pro, rear camera"** → THE most important token for phone-camera authenticity
- **"slight motion blur"** → mimics a real snapshot, not a posed photo
- **"visible skin pores, peach fuzz on jaw, catchlight in eyes"** → anti-plastic trio
- **"9:16 aspect ratio"** → vertical for phone feed (never 1:1 — looks like passport)
- **"No text"** → explicit, so Nano Banana doesn't try to render a caption
- **"supermodel look"** in negatives → extra insurance against idealization

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
