# Skin Texture — Anti-Plastic Tokens

Plastic skin is the single biggest tell that an image was AI-generated.
Nano Banana defaults to "smoothed, retouched, editorial" because that's
what its training data skews toward. You have to explicitly force it
to render micro-details.

---

## The rule

Without explicit texture tokens, the model interprets "realistic" as "idealized."
The word "realistic" alone means nothing to the model after millions of uses.

**Always include at least 2 texture tokens** for any photorealistic-person prompt.

---

## Tier 1 — Essential texture tokens

Include at least one from this tier in every prompt:

```
visible skin pores
natural pore density
peach fuzz on cheek and jaw
slight skin texture
```

These force the model to compute light/skin micro-interactions instead of
flat-shading a smoothed surface.

---

## Tier 2 — Eye tokens (critical for close/medium shots)

Dead-looking eyes = AI tell. Always add:

```
cinematic catchlight in eyes
natural specular reflection in iris
pin-sharp eyes with visible catchlight
```

A **catchlight** is the tiny reflection of the light source visible in the iris.
Every real photograph has them. AI often omits them → "doll eyes."

---

## Tier 3 — Imperfection / asymmetry

Humans are asymmetric. AI defaults to symmetric. Counter:

```
slight asymmetry in face
uneven stubble
slight crooked smile
tired eyes
dry skin texture at the sides of the nose
slight hyperpigmentation on cheek
faint under-eye shadow
freckle cluster on nose bridge
slight scar over eyebrow
```

Pick ONE (not a list). The point is specificity — a real person has
ONE specific imperfection that grounds them.

---

## Tier 4 — Grain & analog artifacts

Digital AI → perfectly clean. Real photo → has noise/grain/artifacts:

```
slight film grain, ISO 800
subtle JPEG compression artifact
slight chromatic aberration at edges
unedited RAW export, no color grade
slight noise in shadows
minor lens flare in corner
```

**Strong combo for phone-camera vibe:**
`slight motion blur, subtle JPEG compression artifact, slight noise in shadows`

**Strong combo for film vibe:**
`slight film grain, ISO 800, slight chromatic aberration at edges`

---

## Tier 5 — Hair micro-details

Flat hair = AI tell. Counter:

```
flyaway hairs at temple
slight frizz
wet strand across forehead
individual hair strands visible
natural hair asymmetry
```

---

## Composite examples (plug-and-play)

### For a 25-year-old woman, viral hook
```
visible skin pores, peach fuzz on cheek, slight asymmetry in face,
cinematic catchlight in eyes, flyaway hair at temple
```

### For a 35-year-old man, founder portrait
```
visible skin pores, uneven stubble, tired eyes with faint under-eye shadow,
cinematic catchlight in eyes, slight chromatic aberration at edges
```

### For a 60-year-old, editorial
```
deep skin texture with visible pores, natural skin folds and wrinkles,
slight hyperpigmentation on forehead, cinematic catchlight in eyes,
silver hair with individual strands visible
```

---

## What NOT to say

These trigger the smoothed-skin subspace — the opposite of what you want:

```
❌ flawless skin
❌ smooth skin
❌ glowing skin
❌ radiant complexion
❌ porcelain skin
❌ perfect complexion
❌ beauty filter
❌ soft skin
```

---

## The physics reason this works

When you specify "pore density" or "peach fuzz," you're forcing Nano Banana to
calculate light interaction at microscopic scale. The model has this capability
but doesn't use it by default because its training data's most common
distribution is retouched photos with those details removed.

By explicitly naming micro-features, you move the generation out of the
"smooth statistical average" region of the latent space into a region where
the training data includes unretouched photos — which look like real humans.

This is why "realistic" alone fails: the model maps "realistic" onto its most
common "this is what the user probably wants" distribution, which is retouched
editorial. You have to name the specific signals that push it elsewhere.
