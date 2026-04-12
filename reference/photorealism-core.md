# Core Photorealism Algorithm

This is the 5-layer prompt structure. Every photorealistic-person prompt should
pass through these 5 layers before you send it to Nano Banana.

---

## The 5 layers (in order)

```
1. SUBJECT          → who + asymmetry
2. ENVIRONMENT      → where + grounding details
3. CAMERA           → hardware reference
4. LIGHTING         → directional + time
5. TEXTURE & GRAIN  → anti-plastic tokens
+ NEGATIVE CONSTRAINTS
```

Each layer contributes a counter-signal that pushes Nano Banana away from its
"AI aesthetic" default. Skip a layer → it regresses toward slop.

---

## Layer 1 — SUBJECT

**Goal:** Real person, not an AI composite of "average attractive."

### Required elements
- Specific age (`28-year-old`, not `young`)
- Clothing described as **lived-in**, not styled
- At least ONE imperfection or asymmetry
- Activity or posture (not "posing")

### Tokens that work
```
uneven stubble
tired eyes
slight crooked smile
damp hair
slight asymmetry in face
scuffed shoes
wrinkled sweater
```

### Tokens to NEVER use
```
beautiful, stunning, perfect, attractive, handsome, gorgeous,
flawless, symmetric, model-like, photogenic, picture-perfect
```

Every one of these triggers the idealization subspace of the model's training data
and pulls you back toward stock-photo land.

### Examples
✅ `A 28-year-old man with uneven stubble and tired eyes, wearing a slightly wrinkled grey hoodie`
❌ `A handsome young man in a stylish sweater, perfect jawline`

---

## Layer 2 — ENVIRONMENT

**Goal:** Grounded in reality. AI needs anchors.

### Required elements
- A real, specific place (neighborhood, type of room, city)
- 1–2 scene props the model can render
- Avoid "minimalist" or "abstract" backgrounds for real-person hooks — those
  scream studio/AI to viewers

### Tokens that work
```
crowded morning metro platform in Barcelona
kitchen with a half-empty coffee mug and a folded newspaper on the counter
cluttered desk with two monitors and a plant in the corner
sun-bleached stone wall in a narrow Mediterranean alley
rubber gym floor with a loaded barbell behind
```

### Anti-pattern
```
❌ "in a modern minimalist space"
❌ "against a clean background"
❌ "studio backdrop"
```

These are what Nano Banana defaults to, which is exactly where you don't want to be.

---

## Layer 3 — CAMERA

**Goal:** Pull the generation from the "studio/editorial" subspace into the
"real-life photography" subspace.

This is the single highest-leverage layer. Getting this right alone removes
~40% of the AI look.

### The four go-to tokens

| Token | Best for |
|---|---|
| `shot on iPhone 15 Pro, rear camera, candid` | Viral social, authentic phone look |
| `35mm f/1.8, slight vignette` | Indie film, warm, lived-in |
| `85mm f/1.4, shallow depth of field` | Editorial portrait, isolated subject |
| `Hasselblad X2D, 135mm, medium format` | High-end editorial, dense texture |

### Film stock tokens (bonus realism)
```
shot on Kodak Portra 400, 35mm film
Fuji C200, natural tones
Ilford HP5, black and white grain
```

### Don't combine multiple camera tokens
The model averages them and gets confused. Pick one and commit.

---

## Layer 4 — LIGHTING

**Goal:** Direction, specificity, time-of-day. Never just "natural light."

### Template
`{DIRECTION} {QUALITY} {TIME OF DAY}, {SHADOW DESCRIPTION}`

### Examples
```
soft window light from the left, natural shadow on right side of face
overcast outdoor light, even diffusion, no hard shadows
morning backlight, rim light on hair, face in open shade
golden hour sidelight at 45 degrees, warm tones, long shadows
harsh iPhone flash, slight red-eye, shadow behind subject
late afternoon sun through blinds, horizontal stripes of light on wall
```

### What NOT to say
```
❌ natural lighting
❌ good lighting
❌ beautiful light
❌ professional lighting
```

These are semantic nulls to Nano Banana. They evaluate to "whatever is average,"
which is the AI-slop regression.

---

## Layer 5 — TEXTURE & GRAIN

**Goal:** Kill plastic skin. Force the model to render micro-details.

Include at least **2** of these in every photorealistic-person prompt:

```
visible skin pores
peach fuzz on cheek and jaw
natural pore density
slight asymmetry in face
cinematic catchlight in eyes
natural specular reflection in iris
pin-sharp eyes with visible catchlight
slight film grain, ISO 800
unedited RAW export, no color grade
subtle JPEG compression artifact
slight chromatic aberration at edges
```

### The catchlight rule
A catchlight is the tiny reflection of the light source visible in the iris.
Real photos have them. AI-rendered eyes without catchlights look dead.
**Always include** `cinematic catchlight in eyes` for close-up or medium shots.

---

## Negative constraints (always append)

Paste this block at the end of every prompt:

```
Avoid: smooth skin filter, beauty retouch, plastic skin texture, symmetrical
face, airbrushed look, HDR glow, digital sheen, over-saturated colors, AI
aesthetic, doll-like eyes, waxy appearance, bloated face, flat eyes,
over-retouched, generic stock photo feel.
```

Adjust with context-specific negatives:
- For viral social: add `influencer look, supermodel look, filter aesthetic`
- For founders: add `LinkedIn headshot polish, corporate portrait feel`
- For lifestyle: add `magazine editorial, over-curated`

---

## Full assembled example

Here's what all 5 layers look like when combined, for the user's ski-slope
finance-creator use case:

```
[Subject]     A 24-year-old man in a brown puffer jacket and white beanie,
              slight crooked smile, slight asymmetry in face,
[Environment] standing on a snowy mountain terrace with ski lifts and fog
              in the background,
[Lighting]    overcast alpine light, soft diffusion, no hard shadows,
[Camera]      shot on iPhone 15 Pro, rear camera, slight motion blur,
[Texture]     visible skin pores, peach fuzz on jaw, cinematic catchlight in eyes,
              9:16 aspect ratio. No text, no captions, no writing in the image.
[Negatives]   Avoid: smooth skin filter, beauty retouch, plastic skin,
              airbrushed, symmetrical face, HDR glow, AI aesthetic, stock
              photo feel, supermodel look.
```

Word count: 57. In the sweet spot (20–60).

---

## What happens if you skip layers

| Skipped | Result |
|---|---|
| Subject imperfection | Idealized AI face |
| Environment specificity | Generic studio backdrop |
| Camera token | Studio portrait look, not phone candid |
| Directional lighting | Flat, even, lifeless |
| Texture tokens | Plastic skin, doll eyes |
| Negative constraints | Regression toward AI aesthetic |

The second screenshot the user showed ("I'D START INVESTING LIKE THIS...")
skipped at least Camera, Texture, and Negatives. The result: classic AI-slop
face, garbled text overlay (because text was in the prompt).

The first screenshot (the ski-slope guy): someone got this right. Probably
a real photo, but if you wanted to replicate it with Nano Banana, the full
5-layer prompt above would get you extremely close.
