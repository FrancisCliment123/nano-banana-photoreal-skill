# Negative Prompts (Exclusion Blocks)

Nano Banana respects negative constraints in the form `Avoid: X, Y, Z`.
These block the default regression toward AI aesthetic.

**Always include a negative block** at the end of every photorealistic-person prompt.

---

## The universal default block

Paste this at the end of any photorealistic-person prompt:

```
Avoid: smooth skin filter, beauty retouch, plastic skin texture, symmetrical
face, airbrushed look, HDR glow, digital sheen, over-saturated colors, AI
aesthetic, doll-like eyes, waxy appearance, bloated face, flat eyes,
over-retouched, generic stock photo feel.
```

---

## Context-specific additions

Stack these onto the default depending on what you're generating.

### For viral social / Instagram hook
Add:
```
, influencer look, supermodel look, filter aesthetic, Facetune look,
Instagram preset
```

Full block for viral social:
```
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
symmetrical face, HDR glow, AI aesthetic, stock photo feel, influencer
look, supermodel look, filter aesthetic.
```

### For founder / professional portrait
Add:
```
, LinkedIn headshot polish, corporate portrait feel, overly groomed,
generic businessperson, stiff posing
```

### For lifestyle / travel
Add:
```
, magazine editorial, over-curated, travel ad feel, influencer aesthetic,
photoshoot energy
```

### For fitness / sport
Add:
```
, fitness model look, commercial sports ad, before-and-after ad,
perfect physique
```

---

## What each negative token does

| Negative | Blocks... |
|---|---|
| `smooth skin filter` | Facetune-style skin smoothing |
| `beauty retouch` | Professional retouching pass |
| `plastic skin texture` | Waxy, polymerized skin look |
| `symmetrical face` | Perfectly mirrored facial features |
| `airbrushed look` | Painted/fashion-mag over-processing |
| `HDR glow` | Over-processed HDR halo around subject |
| `digital sheen` | That specific AI plastic-glow finish |
| `over-saturated colors` | Cartoonish color pop |
| `AI aesthetic` | The generic "this was made by AI" feel |
| `doll-like eyes` | Glazed, lifeless, too-round eyes |
| `waxy appearance` | Low-poly 3D-render feel |
| `bloated face` | AI tendency to add facial fullness |
| `flat eyes` | No catchlight, no life |
| `over-retouched` | Generic polish |
| `stock photo feel` | Shutterstock-grade genericness |

---

## The `supermodel look` problem

Nano Banana has a strong bias toward attractive faces even when you don't
ask for them. If your subject keeps coming out too good-looking for the
scenario, add:

```
supermodel look, fashion model face, idealized features, commercial beauty standard
```

---

## Negative prompts you should NOT use

These are from older diffusion models (Stable Diffusion / SDXL) and either
do nothing or hurt Nano Banana:

```
❌ bad anatomy, bad hands, extra fingers, worst quality, low quality
❌ lowres, blurry, jpeg artifacts
❌ weighted syntax like (bad hands:1.4)
❌ deformed, disfigured, mutated
```

Nano Banana is a different architecture. These tokens were compensating for
diffusion-model failures that Nano Banana doesn't have (to the same degree).
Including them just adds noise.

---

## The anatomical negatives (for hands, which still fail sometimes)

If you're including hands in frame and they keep coming out wrong, use:

```
Avoid: distorted hands, extra fingers, missing fingers, fused fingers,
unnatural finger proportions
```

Better: **reframe to crop hands out**, or generate at 2K+ resolution where
hand detail is more reliable.

---

## Copy-paste blocks

### Viral social hook (user's #1 use case)
```
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
symmetrical face, HDR glow, AI aesthetic, stock photo feel, supermodel
look, filter aesthetic, Facetune look.
```

### Founder / LinkedIn-ish portrait
```
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
symmetrical face, HDR glow, AI aesthetic, LinkedIn headshot polish,
corporate portrait feel, stiff posing, overly groomed.
```

### Travel / lifestyle
```
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed,
symmetrical face, HDR glow, AI aesthetic, magazine editorial, travel ad
feel, over-curated, influencer aesthetic.
```

### Editorial / fashion (when you DO want some polish, but real)
```
Avoid: smooth skin filter, Facetune look, plastic skin, airbrushed, AI
aesthetic, doll-like eyes, waxy appearance.
```
