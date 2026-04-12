# Camera-Roll Energy — The Real Anti-Slop Layer

**This is the single most important lesson in the whole skill.**

You can hit every layer of the 5-layer algorithm (subject, environment, camera,
lighting, texture) and *still* produce a photo that screams "staged AI image."
Why? Because the model defaults to **photographer moves**, even when you ask for
"candid phone photo."

The fix: explicitly block photographer moves and add **friend-took-this-without-telling-me** moves.

---

## The photographer-vs-friend spectrum

Every element in your prompt lives on this spectrum:

```
┌─ PHOTOGRAPHER MOVES ─────────────┬─ CAMERA-ROLL MOVES ────────────┐
│ Golden hour sidelight            │ Flat overcast midday light     │
│ Shallow depth of field / bokeh   │ Everything mostly in focus     │
│ Centered subject                 │ Off-center, slightly tilted    │
│ Subject facing camera            │ Subject looking at phone / off │
│ Clean / minimalist background    │ Cluttered, real street mess    │
│ Slight smile / posed expression  │ Mid-action, not aware of camera│
│ Styled outfit                    │ Wrinkled / basic clothes       │
│ Rule of thirds composition       │ Subject wherever they landed   │
│ Rim light on subject             │ Flat ambient light on everyone │
│ "85mm f/1.4"                     │ "iPhone 13, rear camera"       │
│ Expressive / performative pose   │ Slouched, slight slouch        │
│ Polished smile                   │ Neutral / tired / concentrated │
└──────────────────────────────────┴────────────────────────────────┘
    = "this was TAKEN of me"         = "this was SNAPPED of me"
    = viewer reads AI / produced     = viewer reads real person
```

**Rule:** for viral social content, every slider should be pushed to the
right (camera-roll side).

---

## Why the model defaults to photographer moves

Its training data for "person in a city" includes:
- Stock photography (photographer moves)
- Magazine editorials (photographer moves)
- Ad campaigns (photographer moves)
- Travel blog photos (photographer moves)
- Instagram influencer photoshoots (photographer moves)

Only a small fraction is actual candid camera-roll content. Left to its own,
it statistically averages toward the photographer distribution.

You have to **explicitly name the camera-roll moves** to pull it into the
other distribution.

---

## The 7 camera-roll tokens to always include

Use at least **5** of these in any viral-hook prompt:

### 1. Kill golden hour
```
flat overcast midday light, no golden hour, no rim light, even dull diffusion
cool overcast afternoon light, flat shadows
harsh fluorescent overhead light (for indoor)
```

### 2. Kill shallow depth of field
```
everything mostly in focus, no bokeh, flat depth
deep depth of field, background sharp
wide-angle perspective, no subject isolation
```

### 3. Kill the posed expression
Pick ONE, and the subject should NOT be facing the camera:
```
looking down at his phone in one hand, not facing the camera
looking off-frame at something left of view
mid-sentence talking to someone out of frame
concentrated expression on laptop, unaware of camera
slight yawn, eyes half-closed
```

### 4. Add background clutter
The background should NOT be clean. Name 2–3 messy elements:
```
other pedestrians slightly visible in the background, some out of focus,
a bus passing behind, a trash bin on the left edge of frame
a blurred couple walking past, a parked scooter leaning against a wall,
a crumpled paper bag on the ground
```

### 5. Kill centered composition
```
off-center composition with subject in right half
subject in lower-left third, top of frame empty sky
handheld shaky framing slightly tilted
crooked horizon line
```

### 6. Add amateur framing
```
handheld shaky framing slightly tilted
awkward angle, shot from hip-level
edge of frame clips shoulder
slight lens distortion at edges
```

### 7. Compression artifacts (iPhone JPEG authenticity)
```
visible JPEG compression artifacts
slight noise in shadows
minor color banding in sky
iPhone HDR slightly over-blown highlights
```

---

## The expanded negative block for viral social

In addition to the default negatives, stack these:

```
Avoid: ... [standard negatives] ..., male model look, magazine cover,
centered composition, golden hour, bokeh background, shallow depth of
field, styled outfit, posed, photoshoot energy, professional photograph,
rim light on subject, rule of thirds framing, subject facing camera,
clean background.
```

---

## Full worked prompt (this is what nailed the user's "camera-roll" test)

```
Random iPhone snapshot of a 28-year-old man in a slightly wrinkled grey hoodie
and faded black jeans, mid-stride on a crowded Barcelona sidewalk, looking
down at his phone in one hand, slight slouch, other hand holding a takeaway
coffee cup, not facing the camera.

Other pedestrians slightly visible in the background, some out of focus,
a bus passing behind, a trash bin on the left edge of frame.

Flat overcast midday light, no golden hour, no rim light, even dull diffusion.

Shot on iPhone 13, rear camera, handheld shaky framing slightly tilted,
visible JPEG compression artifacts, slight motion blur on hand and phone,
slight noise in shadows, visible skin pores, uneven stubble with patchy
growth, slight under-eye shadow, faint asymmetry in face.

Off-center composition with subject in right half. 9:16 aspect ratio.
No text, no captions, no readable signs.

Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
symmetrical face, HDR glow, AI aesthetic, stock photo feel, supermodel
look, male model look, professional photograph, magazine cover, centered
composition, golden hour, bokeh background, shallow depth of field,
styled outfit, posed, photoshoot energy.
```

**Why it works:** every sentence is pushing right on the spectrum. No
single token does the work — it's the cumulative effect of 5+ camera-roll
moves plus an expanded negative block.

---

## Quick test: is your prompt camera-roll or photographer?

Look at your draft prompt. Count the moves:

**Photographer moves (bad for viral social):**
- [ ] Golden hour / rim light / beautiful light
- [ ] 85mm / shallow DoF / bokeh
- [ ] Centered / rule of thirds
- [ ] Subject facing camera / smiling
- [ ] Clean / minimalist background
- [ ] Styled outfit

**Camera-roll moves (good for viral social):**
- [ ] Flat / overcast / dull light
- [ ] Everything in focus / no bokeh
- [ ] Off-center / tilted / amateur framing
- [ ] Subject looking at phone / off-frame / unaware
- [ ] Cluttered / messy background with extras
- [ ] Wrinkled / basic / lived-in clothes

**Rule:** if your camera-roll count isn't at least 4, your image will look staged.

---

## When to NOT use camera-roll energy

Some scenarios still want photographer moves:
- **Editorial portraits** (About page, press photo)
- **Fashion / beauty content** (where polish is the point)
- **Product shots with a human**
- **Testimonial / quote cards** where the person is clearly a subject

For everything else in social media — **especially viral hooks** — push hard into camera-roll territory.

---

## The before/after test (from the user's actual iteration)

**v1 prompt (photographer energy):**
> "walking down a sunlit Barcelona side-street... slight side glance with subtle
> smile... late morning golden hour sidelight, warm golden tones, long shadow
> on cobblestones..."

Result: handsome guy in a coat, golden light, looking at camera, smiling.
Looked like a tourism ad.

**v2 prompt (camera-roll energy):**
> "mid-stride on a crowded Barcelona sidewalk, looking down at his phone in
> one hand, slight slouch... pedestrians in the background, a bus passing
> behind, trash bin on left edge... flat overcast midday light, no golden
> hour... handheld shaky framing slightly tilted..."

Result: guy in a hoodie looking at his phone, real street mess around him,
boring light, off-center framing.
Looked like a real snapshot.

**The photo quality didn't change. The direction of intent did.**
