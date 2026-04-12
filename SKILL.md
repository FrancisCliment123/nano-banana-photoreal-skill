---
name: nano-banana-photoreal
version: "1.0.0"
description: "Prompt engineering for photorealistic people in Nano Banana (Gemini 2.5 / 3 Pro Flash Image). Stops AI slop — plastic skin, doll faces, garbled text — and produces viral-quality social media hook images that look like real phone photos, not AI generations. Includes template library for common scenarios (viral hook, candid selfie, founder portrait, travel, lifestyle) and reference guides on camera tokens, lighting, skin texture, negative prompts, and the two-step text rendering method. TRIGGER: nano banana, gemini image, photorealistic person, ai photo real, viral hook image, carousel cover, avoid ai slop, plastic skin, fake looking photo, instagram hook image."
argument-hint: 'nano-banana-photoreal build <concept>'
allowed-tools: Read, Write, Bash
user-invocable: true
author: FrancisCliment123
license: MIT
homepage: https://github.com/FrancisCliment123/nano-banana-photoreal-skill
repository: https://github.com/FrancisCliment123/nano-banana-photoreal-skill
metadata:
  openclaw:
    emoji: "🍌"
    tags:
      - nano-banana
      - gemini
      - image-generation
      - photorealism
      - prompt-engineering
      - instagram
      - viral-hooks
---

# Nano Banana Photoreal — Stop Generating AI Slop

Nano Banana (Gemini 2.5/3 Flash Image) is powerful but defaults to "AI aesthetic":
plastic skin, doll-like eyes, symmetric faces, smooth-everything, and garbled text overlays.
This skill is the playbook that fixes that.

**Use this skill whenever you're about to generate an image with a real-looking person** —
especially for viral social media hooks, carousel covers, ads, or founder portraits.

---

## When this skill activates

Read this skill when the user asks for any of these:

- Generate a photorealistic person with Nano Banana / Gemini
- Create a viral Instagram / TikTok hook image
- Improve an existing prompt that's producing AI-looking results
- Fix "plastic skin," "doll face," "AI slop," fake-looking photos
- Build a carousel cover or story slide with a real person on it
- Write a prompt for Gemini 2.5 Flash Image / Gemini 3 Pro Flash Image

---

## The 30-second decision tree

```
User wants an image with a person?
│
├── Needs text overlay in the image?
│   │
│   ├── YES → Use the TWO-STEP METHOD (see reference/text-rendering.md)
│   │         1. Generate photo-only with Nano Banana (no text)
│   │         2. Overlay text separately in Canva/Figma/sharp/Photoshop
│   │         → Why: Nano Banana still mangles text (see second user screenshot)
│   │
│   └── NO → Just prompt normally, skip this branch
│
└── Is it a social media hook (Instagram / TikTok / Reels)?
    │
    ├── YES → Use templates/viral-hook-real-person.md
    │         Emphasize AUTHENTICITY (iPhone, candid, imperfection)
    │         Reference: photorealism-core.md + skin-texture.md
    │
    └── NO  → Pick the closest template:
              - candid-phone-selfie.md (casual lifestyle)
              - founder-working.md (LinkedIn / professional)
              - travel-candid.md (outdoor / environmental)
              - lifestyle-portrait.md (editorial / curated)
```

---

## The core algorithm for building a Nano Banana prompt

Every photorealistic-person prompt you write should follow this 5-layer structure.
Skip a layer and you drift toward AI slop.

```
┌─────────────────────────────────────────────┐
│  LAYER 1 — SUBJECT (who, with asymmetry)    │
│  LAYER 2 — ENVIRONMENT (where, grounded)    │
│  LAYER 3 — CAMERA (hardware reference)      │
│  LAYER 4 — LIGHTING (directional, specific) │
│  LAYER 5 — TEXTURE/GRAIN (anti-plastic)     │
│  + NEGATIVE CONSTRAINTS                     │
└─────────────────────────────────────────────┘
```

### Layer 1 — Subject
- Specify real, asymmetric features. "A 28-year-old man with uneven stubble, tired eyes"
  beats "a handsome young man."
- Clothing should be lived-in, not styled. "slightly wrinkled grey hoodie" beats "stylish outfit."
- Never use: "beautiful," "perfect," "attractive," "stunning," "handsome" (these trigger AI idealization).

### Layer 2 — Environment
- Specific, not generic. "crowded morning metro platform in Barcelona" beats "city street."
- Include 1–2 grounding environmental details the AI can render (coffee cup, scuffed wall,
  folded newspaper).

### Layer 3 — Camera hardware (critical — this alone removes 40% of AI look)
Pick ONE and commit to it:

| Token | What it produces |
|---|---|
| `shot on iPhone 15 Pro, rear camera, candid` | Digital noise, phone authenticity, slight compression |
| `35mm f/1.8, slight vignette` | Warm grain, indie film feel |
| `85mm f/1.4, shallow depth of field` | Portrait compression, bokeh, editorial |
| `Hasselblad X2D, 135mm, medium format` | Dense texture, high dynamic range, fashion/editorial |
| `shot on Kodak Portra 400, 35mm film` | Film stock look, natural skin tones |
| `Sony A7R IV, 50mm f/1.8` | Crisp modern digital, versatile |

### Layer 4 — Lighting (directional, never "natural lighting" alone)
Always say WHERE the light comes from:
- `soft window light from the left, natural shadow on right side of face`
- `overcast outdoor light, even diffusion, no hard shadows`
- `morning backlight, rim light on hair, face in open shade`
- `golden hour sidelight at 45 degrees, warm tones, long shadows`
- `harsh iPhone flash, slight red-eye, shadow behind subject` (for gritty authentic look)

### Layer 5 — Texture & grain (anti-plastic)
Include at least 2 of these:
- `visible skin pores`
- `peach fuzz on cheek and jaw`
- `slight asymmetry in face`
- `natural pore density`
- `cinematic catchlight in eyes` (tiny reflection of light source in iris — makes eyes alive)
- `slight film grain, ISO 800`
- `unedited RAW export, no color grade`
- `subtle JPEG compression artifact` (for phone-camera look)

### Negative constraints (always include)
Paste this block at the end of every photorealistic-person prompt:

```
Avoid: smooth skin filter, beauty retouch, plastic skin texture, symmetrical face,
airbrushed look, HDR glow, digital sheen, over-saturated colors, AI aesthetic,
doll-like eyes, waxy appearance, bloated face, flat eyes, over-retouched,
generic stock photo feel.
```

---

## Prompt length discipline

**Sweet spot: 20–60 words, 2–4 sentences.**

- Under 20 words → too vague, AI fills in generic defaults.
- Over 60 words → model loses focus, ignores later tokens.
- More than 5 adjectives per noun → scores drop sharply.
- NEVER use weighted tokens like `(pore density:1.4)` — actively hurts Nano Banana.
- NEVER use quality boosters like "masterpiece, 8K, trending on ArtStation" — diffusion-era
  legacy that Nano Banana's architecture ignores or treats as noise.

---

## Common failure modes (diagnose before re-rolling)

| Symptom | Root cause | Fix |
|---|---|---|
| Plastic skin, "AI sheen" | Missing texture tokens | Add `visible skin pores`, `peach fuzz`, `no beauty retouch` |
| Face too symmetric, doll-like | Missing asymmetry hint | Add `slight asymmetry in face`, `uneven stubble`, `tired eyes` |
| Eyes look dead / glazed | No catchlight | Add `cinematic catchlight in eyes`, `natural specular reflection in iris` |
| Garbled text in image | Generated text in prompt | Remove text from prompt, overlay in post-production |
| Looks like stock photo | Subject too generic | Add 1 specific imperfection + grounded environment detail |
| Hands wrong | Hands in prompt + low resolution | Either reframe to crop hands, or add `natural hand proportions, five fingers visible` + generate at 2K+ |
| Background too clean | No environmental specificity | Name a real place, add 1–2 scene props |

---

## Text overlay — the non-negotiable rule

Nano Banana mangles text. Look at the user's own screenshot:
`"TIY ADMN FROM 0 AGAIN"` was supposed to be `"DIY AGAIN FROM 0"`.

**Never generate text in the image for:**
- Anything longer than 5 words
- Anything with numbers
- Headlines, captions, overlay text
- Brand names

**Instead, two-step:**
1. Generate a clean image with Nano Banana, explicitly say `no text, no captions, no writing in the image`.
2. Overlay text after with one of:
   - Canva / Figma (manual)
   - `sharp` Node.js library (programmatic, already in many projects)
   - CSS/HTML rendering to image (for web-based pipelines)

See `reference/text-rendering.md` for code examples.

---

## How to use this skill programmatically

Read the template that matches the scenario, then read 1–2 reference files, then
construct the prompt using the 5-layer structure.

```
# Example: user asks for a viral finance hook image
1. Read templates/viral-hook-real-person.md
2. Read reference/skin-texture.md
3. Read reference/negative-prompts.md
4. Fill in the template's blanks with user's specifics
5. Emit final prompt (20–60 words) + note that text must be added separately
```

---

## File index

```
SKILL.md                    ← you are here
README.md                   ← GitHub landing page

templates/
  viral-hook-real-person.md       ← Instagram/TikTok hook images (user's #1 use case)
  candid-phone-selfie.md          ← Amateur phone snapshot aesthetic
  founder-working.md              ← LinkedIn / professional portrait
  travel-candid.md                ← Outdoor / environmental lifestyle
  lifestyle-portrait.md           ← Editorial / curated lifestyle

reference/
  photorealism-core.md            ← The 5-layer algorithm in depth
  camera-roll-energy.md           ← CRITICAL: kill photographer moves for viral social
  camera-tokens.md                ← Every camera/lens token and what it does
  lighting-tokens.md              ← Directional lighting vocabulary
  skin-texture.md                 ← Anti-plastic skin tokens
  negative-prompts.md             ← Copy-paste exclusion blocks
  text-rendering.md               ← The two-step method + code

scripts/
  add-hook-text.js                ← Playwright overlay for Step 2 (hook text on photo)

examples/
  bad-vs-good.md                  ← Before/after comparison of real prompts
  viral-hook-library.md           ← 20+ ready-to-adapt hook prompts
```

---

## Credits & further reading

Built from synthesis of:
- Google Cloud's official Nano Banana prompting guide
- Nano Banana 2 fal.ai technical guide
- Atlabs AI prompting framework (the 5-layer structure)
- CookedBanana's plastic skin fix methodology
- Stockimg.ai advanced photorealism techniques

License: MIT
