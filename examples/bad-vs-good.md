# Bad vs Good — Side by Side

Concrete diagnosis of real AI-slop prompts vs fixed versions.
Based on the user's own viral-post comparison.

---

## Case 1 — The user's screenshot pair

### Screenshot A (GOOD — looks real)
A 24-year-old guy on a snowy ski slope, winter jacket, relaxed posture,
slight smile. Bold white uppercase text on top: "HOW TO START INVESTING
STEP BY STEP — from a 24 year old who built a 6-figure portfolio."

This was almost certainly a **real photo**, but to replicate it with Nano Banana:

**Good prompt:**
```
Candid iPhone photo of a 24-year-old man in a brown puffer jacket and white
beanie, standing on a snowy mountain terrace with ski lifts and fog in the
background, slight crooked smile, hands relaxed at sides. Overcast alpine
light, soft diffusion, no hard shadows. Shot on iPhone 15 Pro, rear camera,
slight motion blur, visible skin pores, peach fuzz on jaw, cinematic
catchlight in eyes, slight asymmetry in face. 9:16 aspect ratio.
No text, no captions, no writing in the image.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
symmetrical face, HDR glow, AI aesthetic, stock photo feel, supermodel look.
```

Word count: 86. A bit long, but every token earns its place.
Then overlay the hook text in Canva / via `sharp` / via Puppeteer.

---

### Screenshot B (BAD — AI slop)
An obvious AI-generated man in a grey blazer leaning on a desk in a cafe,
with garbled text on top: `"I'D START INVESTING LIKE THIS IF I HAD TIY ADMN FROM 0 AGAIN"`

**What probably went wrong:**

The prompt was likely something like:
```
Create an image of a young man in a blazer in a modern cafe with the text
"I'D START INVESTING LIKE THIS IF I HAD TO DIY AGAIN FROM 0" on top,
for Instagram.
```

**Everything wrong with it:**

1. ❌ **Text in the prompt** — Nano Banana garbled it ("TIY ADMN")
2. ❌ **"young man"** — triggers idealization, got a model-looking face
3. ❌ **"in a blazer"** — styled, not lived-in clothes
4. ❌ **"modern cafe"** — generic, no grounding
5. ❌ **No camera token** — defaulted to studio/editorial look
6. ❌ **No lighting direction** — got flat, even, AI lighting
7. ❌ **No texture tokens** — got plastic skin
8. ❌ **No negative constraints** — no block against AI aesthetic

**Fixed version:**

```
Candid photo of a 27-year-old man in a wrinkled grey t-shirt under an open
navy overshirt, sitting at a small wooden cafe table in a narrow Lisbon
side-street cafe, laptop open, mug in hand mid-sip, slight tired smile.
Late morning side light from the street, warm golden tones, soft shadow
on right side of face. Shot on 35mm f/1.8, slight vignette, visible skin
pores, uneven stubble, cinematic catchlight in eyes, slight asymmetry in
face. No text, no captions, no writing on laptop screen or menu visible.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
symmetrical face, AI aesthetic, stock cafe photo, LinkedIn polish,
model look.
```

Then the hook text `"I'D START INVESTING LIKE THIS IF I HAD TO DIY AGAIN FROM 0"`
goes on top in post-production. Nano Banana never touches it, so it can't
garble it.

---

## Case 2 — Typical "AI founder portrait" fail

### BAD prompt
```
A successful young entrepreneur in a suit standing in a modern office,
looking confident, professional lighting, 4K, masterpiece, trending on
ArtStation, best quality.
```

**Why it fails:**
- `successful young entrepreneur` → generic stock-photo trigger
- `in a suit` → styled
- `modern office` → no grounding
- `looking confident` → AI's interpretation = stiff, posed
- `professional lighting` → semantic null
- `4K, masterpiece, trending on ArtStation, best quality` → diffusion-era legacy
  tokens, Nano Banana ignores or treats as noise

### GOOD prompt
```
Candid photo of a 33-year-old man in a wrinkled grey t-shirt and unshaven
jaw, standing in a small cluttered office with a whiteboard covered in
diagrams behind him, arms loose at sides, slight tired smile. Soft
afternoon window light from the left, natural shadow on right side of
face. Shot on 35mm f/1.8, slight vignette, visible skin pores, peach fuzz
on jaw, cinematic catchlight in eyes, slight asymmetry in face.
No text, no readable writing on whiteboard.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
LinkedIn headshot polish, corporate portrait feel, stiff posing,
AI aesthetic.
```

---

## Case 3 — The "Instagram influencer" trap

### BAD prompt
```
Beautiful woman drinking coffee in a chic cafe, Instagram aesthetic,
soft lighting, cinematic.
```

**Why it fails:**
- `beautiful` → pulls straight into idealized face
- `chic cafe` → Pinterest-style generic
- `Instagram aesthetic` → the model's interpretation is literally "Instagram filter"
- `soft lighting, cinematic` → semantic nulls

### GOOD prompt
```
Candid iPhone photo of a 28-year-old woman in a faded grey sweatshirt,
sitting at a small cafe table with a half-empty mug and an open paperback
book, slight smile at something off-frame, flyaway hair, tired eyes.
Warm morning window light from the right, natural shadow on left side
of face. Shot on iPhone 15 Pro, rear camera, slight motion blur, visible
skin pores, peach fuzz on cheek, cinematic catchlight in eyes, slight
asymmetry in face. 9:16 aspect ratio. No text, no captions, no book
title visible.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
influencer aesthetic, Facetune look, supermodel face, AI aesthetic.
```

---

## Key diagnosis rules (fast lookup)

If your output has... | Add to the prompt
---|---
Plastic / waxy skin | `visible skin pores, peach fuzz, no beauty retouch`
Dead / doll eyes | `cinematic catchlight in eyes, natural specular reflection in iris`
Too symmetric face | `slight asymmetry in face, uneven stubble / slight crooked smile`
Looks like a model | Remove any positive adjective. Add imperfection + negative `supermodel look`
Studio feel | Add camera token (iPhone 15 Pro / 35mm) + specific real location
Garbled text | Remove text from prompt, overlay in post
Generic location | Name a specific real place (neighborhood, city)
Posed, stiff | Add `candid`, `slight motion blur`, `mid-action` verb

---

## The final sanity check

Before sending a prompt to Nano Banana, ask yourself:

- [ ] Does it have a camera hardware token?
- [ ] Does it have directional lighting (not "natural light")?
- [ ] Does it have at least 2 texture tokens?
- [ ] Does the subject have at least 1 specific imperfection?
- [ ] Is the location specific (named place or concrete detail)?
- [ ] Is it 20–60 words?
- [ ] Is there a `Avoid:` negative block?
- [ ] Is there NO text in the generation (will be added in post)?

If all 8 are yes — send it. If any are no — fix first.
