# Camera & Lens Tokens

The single highest-leverage decision in a Nano Banana photoreal prompt.
Pick ONE token. Commit. Do not stack.

---

## Quick-pick table

| Use case | Token |
|---|---|
| Viral IG/TikTok hook, phone snapshot vibe | `shot on iPhone 15 Pro, rear camera, candid` |
| Indie film / warm lived-in | `35mm f/1.8, slight vignette` |
| Editorial portrait, soft bokeh | `85mm f/1.4, shallow depth of field` |
| High-end editorial, dense texture | `Hasselblad X2D, 135mm, medium format` |
| Crisp modern digital | `Sony A7R IV, 50mm f/1.8` |
| Film stock, natural skin | `shot on Kodak Portra 400, 35mm film` |
| Moody black and white | `Ilford HP5, 35mm film, high contrast` |
| Nostalgic warm faded | `Fuji C200, slightly underexposed` |

---

## Lens-by-focal-length guide

Each focal length compresses the subject differently. The model treats these
as distinct visual styles.

### Wide-angle (18–35mm)
- "Expansive scenes, environmental context"
- Good for: street photography, environmental portraits, lifestyle with setting
- Example token: `35mm f/1.8`

### Standard (50mm)
- "Natural perspective, versatile"
- Good for: everyday shots, mid-distance subjects, snapshots
- Example token: `50mm f/1.8, natural perspective`

### Short telephoto (85–135mm)
- "Subject isolation, portrait compression, professional headshots"
- Good for: editorial portraits, fashion, any close-up where subject must dominate
- Example token: `85mm f/1.4, shallow depth of field`

**Rule of thumb:** Longer focal length → denser texture rendering on the focal point.
Telephoto pulls more plastic-skin-defeating detail than wide-angle.

---

## Aperture guidance

| Aperture | Effect |
|---|---|
| f/1.4–f/2.8 | Shallow DoF, blurred background, cinematic subject isolation |
| f/4–f/5.6 | Balanced focus with context visible |
| f/8–f/16 | Everything sharp, product/landscape depth |

For portraits and social hooks, **f/1.4–f/2.8 is the default**.

---

## Phone camera tokens (for viral social content)

iPhone tokens are special — they pull from a training distribution that's
heavy in candid, imperfect, real-person photos. Use them when you want
authenticity, not editorial polish.

### Strong tokens
```
shot on iPhone 15 Pro, rear camera, candid
iPhone 14 Pro, portrait mode, slight digital noise
shot on iPhone, front camera, awkward angle, slight distortion
```

### Paired with motion/imperfection for extra realism
```
shot on iPhone 15 Pro, rear camera, slight motion blur
iPhone 15 Pro, rear camera, slightly out of focus
shot on iPhone, harsh flash, slight red-eye, uneven framing
```

---

## Film stock tokens (for analog warmth)

Film stocks have distinct color palettes and grain structures Nano Banana
has learned to render.

```
shot on Kodak Portra 400        → natural warm tones, good skin
shot on Kodak Gold 200          → slightly yellow-green, nostalgic
shot on Fuji C200               → green-blue shift, faded
shot on Fuji Pro 400H           → soft pastels, wedding/editorial
shot on Ilford HP5              → black and white, grainy
shot on CineStill 800T          → tungsten-balanced, neon/night
```

### Pair with grain tokens
```
shot on Kodak Portra 400, slight film grain, ISO 800
Ilford HP5, heavy grain, pushed development
```

---

## Advanced: composite camera-lens-film

These three-part tokens stack the strongest realism signals:

```
Shot on Leica M11, 50mm Summilux f/1.4, Kodak Portra 400 emulation
Sony A7R IV, 85mm f/1.4 GM, natural color profile, no grain
Canon 5D Mark IV, 35mm f/1.4, slight vignette, minimal grading
```

Use these when you want **editorial-grade** realism. For viral social, stick
with the simple `iPhone 15 Pro, rear camera, candid` pattern.

---

## Anti-patterns (avoid)

```
❌ shot on a camera
❌ professional camera
❌ high-resolution camera
❌ DSLR (too vague — specify which)
❌ combining multiple cameras in one prompt
❌ weighted syntax like (Kodak Portra 400:1.3)
```

---

## Decision flowchart

```
Is it a social media hook / Instagram / TikTok?
│
├── YES → `shot on iPhone 15 Pro, rear camera, candid`
│         (optionally + slight motion blur for extra candor)
│
└── NO
    │
    ├── Professional portrait (LinkedIn-style, editorial)?
    │   └── `85mm f/1.4, shallow depth of field`
    │
    ├── Street/environmental?
    │   └── `35mm f/1.8, slight vignette`
    │
    ├── Fashion / high-end editorial?
    │   └── `Hasselblad X2D, 135mm, medium format`
    │
    └── Analog warmth?
        └── `shot on Kodak Portra 400, 35mm film`
```
