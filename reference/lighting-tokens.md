# Lighting Tokens

"Natural lighting" is a null token to Nano Banana. Be specific about
**direction, quality, time, and shadow behavior.**

---

## The lighting sentence template

```
{DIRECTION} {QUALITY} {TIME OF DAY}, {SHADOW DESCRIPTION}
```

Example:
```
soft window light from the left, natural shadow on right side of face
```

---

## By scenario

### Indoor morning (lifestyle, cozy)
```
soft window light from the left, morning warm tones, gentle shadow on right side of face
kitchen backlight from east-facing window, steam-diffused, soft shadow
```

### Indoor afternoon (founder, work-from-home)
```
afternoon window light from the side, long horizontal shadows on wall,
face in half-shadow
late afternoon sun through blinds, horizontal stripes of light on wall
```

### Outdoor overcast (authentic candid)
```
overcast outdoor light, even diffusion, no hard shadows
cold overcast afternoon, soft flat light, muted colors
```

### Outdoor golden hour (editorial, travel, aspirational)
```
golden hour sidelight at 45 degrees, warm tones, long shadows
late afternoon sun behind subject, rim light on hair, face in open shade
```

### Outdoor harsh midday (gritty, authentic, summer)
```
harsh midday sun overhead, short deep shadow under chin
direct sunlight from above, squinting eyes, sharp shadow on neck
```

### Night / neon (urban, moody)
```
neon sign backlight, magenta rim on hair, face in soft shadow
street lamp overhead, harsh shadow under eyebrows, cool color temperature
```

### Phone flash (candid party, night-out snapshot)
```
harsh iPhone flash, slight red-eye, shadow behind subject on wall
on-camera flash, flat lighting, slight lens glare
```

### Studio (editorial, when you DO want polish)
```
three-point softbox setup, soft key from left, rim light from behind
```
*Use sparingly — most viral social content is NOT shot in studio.*

---

## By mood

| Mood | Lighting token |
|---|---|
| Warm / intimate | `golden hour sidelight, warm tones` |
| Professional / clean | `soft north-facing window light, even diffusion` |
| Gritty / real | `overcast outdoor light, no hard shadows` |
| Cinematic / dramatic | `single hard sidelight, deep shadow on opposite side` |
| Moody / night | `neon sign backlight, magenta rim on hair` |
| Authentic phone / candid | `harsh iPhone flash, slight red-eye` |
| Editorial / high-end | `three-point softbox setup` |

---

## Catchlight & rim light

Two modifiers that add instant photo-realism to any lighting setup:

### Catchlight (always use for close/medium shots)
```
cinematic catchlight in eyes
natural specular reflection in iris
```

Without this, eyes look dead. With it, eyes look alive.

### Rim light (adds dimension)
```
rim light on hair
subtle edge light on shoulder
backlit halo effect on hair edge
```

Rim light separates the subject from the background and signals "this is a
real photo, shot with intentional lighting."

---

## What to avoid

```
❌ natural lighting          (semantic null)
❌ good lighting             (meaningless)
❌ beautiful lighting        (triggers idealization)
❌ perfect lighting          (triggers idealization)
❌ professional lighting     (generic, drifts to stock)
❌ dramatic lighting         (too vague)
❌ cinematic                 (overused; say HOW)
```

The word `cinematic` alone is overused and has lost meaning. If you want
cinematic, specify WHY: `cinematic sidelight, deep shadow, shallow DoF`.

---

## Advanced: contrast & color temperature

### Contrast tokens
```
high contrast, deep shadows
low contrast, flat diffused light
medium contrast, soft shadow transitions
```

### Color temperature tokens
```
warm 3200K tungsten tones
cool 5600K daylight balance
mixed warm indoor + cool outdoor light through window
neutral color temperature, no color cast
```

These are worth adding when you need color grading control — for example,
to match a brand palette or a specific aesthetic (cozy warm, corporate cool).

---

## Full worked example

**Scenario:** founder portrait at cluttered desk, afternoon.

**Weak:** "natural lighting"

**Strong:**
```
afternoon window light from the left, natural shadow on right side of face,
warm tones, slight rim light on hair from window, cinematic catchlight
in eyes
```

This tells the model: light source position (left), time of day (afternoon),
color temp (warm), secondary effect (rim on hair), and focal detail (catchlight).
All concrete. All renderable.
