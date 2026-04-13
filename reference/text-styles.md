# Text Styles — Exact Font, Size, Weight, Placement

Two text styles are supported by `scripts/add-hook-text.js` and should be used for
different types of content. This reference captures the exact specifications so any
future session can reproduce (or re-implement) the look from scratch.

---

## Style 1 — VIRAL (Instagram/TikTok hook reels)

**Use when:** the goal is to stop the scroll. Loud, uppercase, "this is a hook" energy.
Typical examples: finance advice hooks, fitness transformation hooks, creator
challenge hooks.

### Font
- **Primary:** Anton (Google Fonts — `https://fonts.googleapis.com/css2?family=Anton&display=swap`)
- **Alternatives:** Bebas Neue, Impact (system), Oswald
- All are **tall, condensed display sans-serifs**. Anton is the cleanest/most modern.

### Specs
| Property | Value |
|---|---|
| Font family | `'Anton', 'Impact', 'Arial Narrow', sans-serif` |
| Font weight | 400 (Anton is designed at single weight) |
| Font size | **8% of image width** (e.g. 86px on 1080-wide) |
| Line height | 1.02 (tight) |
| Letter spacing | -0.01em |
| Text transform | UPPERCASE |
| Color | `#FFFFFF` |
| Text shadow | `0 2px 6px rgba(0,0,0,0.45), 0 6px 24px rgba(0,0,0,0.35)` |
| Alignment | center |
| Width | 90% of image width |
| Vertical position | `top` (8% from top) — default |
| Scrim | Yes — top-down gradient `rgba(0,0,0,0.35)` → transparent, 45% tall |

### Example
> `HOW TO START INVESTING STEP BY STEP — from a 24 year old who built a 6-figure portfolio`

### Command
```bash
node scripts/add-hook-text.js \
  --style viral \
  --input photo.png \
  --output final.png \
  --hook "HOW TO START INVESTING STEP BY STEP" \
  --position top \
  --font anton
```

### When NOT to use
- Personal-brand carousels (too loud)
- Editorial content (use gallery instead)
- Long text (4+ lines) — gets cramped in centered uppercase

---

## Style 2 — GALLERY (personal-brand carousels, editorial slides)

**Use when:** the aesthetic is quiet-luxury Instagram carousel. Bold sentence-case title
+ regular-weight body paragraph. Matches the reference examples the user showed:
"Health", "Tech Equipment", "Traveling".

### Font
- **Primary:** Inter (Google Fonts — `https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;800&display=swap`)
- **Alternatives:** SF Pro Display (macOS system), Helvetica Neue, -apple-system
- Inter renders identically to SF Pro and is free. Use Inter.

### Specs — TITLE
| Property | Value |
|---|---|
| Font family | `'Inter', -apple-system, 'SF Pro Display', 'Segoe UI', sans-serif` |
| Font weight | **700** (Bold) |
| Font size | **6.5% of image width** (e.g. 70px on 1080-wide) |
| Line height | 1.05 |
| Letter spacing | -0.02em (slight tighten — Inter at large sizes) |
| Text transform | none (sentence case: `Health`, not `HEALTH`) |
| Color | `#FFFFFF` |
| Text shadow | **none** (image is already dark — shadow would dirty it) |

### Specs — BODY
| Property | Value |
|---|---|
| Font family | (same as title) |
| Font weight | **400** (Regular) |
| Font size | **3.3% of image width** (e.g. 35px on 1080-wide) |
| Line height | 1.35 |
| Letter spacing | -0.005em |
| Color | `#FFFFFF` at 95% opacity (slightly softer than title) |
| Margin below title | ~35% of title font size |

### Layout
| Property | Value |
|---|---|
| Alignment | **left** (matches reference) |
| Text block width | **62% of image width** (for body wrap) |
| Horizontal position | 8% from left edge |
| Vertical position | **30% from top** (upper-middle) OR 10% from top (`--title-position top`) |
| Scrim | **no** (image already has empty dark zone by design — see personal-gallery-aesthetic.md) |

### Example
> **Health**
>
> Health isn't just about the gym. It's also about sleep, good food, and managing your stress levels.

### Command
```bash
node scripts/add-hook-text.js \
  --style gallery \
  --input photo.png \
  --output final.png \
  --hook "Health" \
  --body "Health isn't just about the gym. It's also about sleep, good food, and managing your stress levels." \
  --align left \
  --title-position top
```

### When NOT to use
- Viral hook reels (not loud enough)
- When the image has bright content where text will go (use scrim + shadow via viral style)
- Super long titles (3+ words) — gallery style is label-like

---

## Decision tree

```
What's the image for?
│
├── Scroll-stopping Instagram Reel / TikTok hook
│   → VIRAL style (Anton uppercase, centered, shadow)
│
├── Personal-brand Instagram carousel (educational, editorial)
│   → GALLERY style (Inter bold + body, left-aligned, no shadow)
│
└── LinkedIn quote card / Twitter screenshot-style
    → GALLERY style (same recipe)
```

---

## If you ever need to re-implement from scratch

Here's the minimal HTML/CSS that reproduces each style exactly.

### Viral (reproduce from scratch)
```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Anton&display=swap" />
<style>
  body { position: relative; margin: 0; }
  .bg { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; }
  .scrim { position: absolute; top: 0; left: 0; right: 0; height: 45%;
    background: linear-gradient(180deg, rgba(0,0,0,0.35) 0%, rgba(0,0,0,0) 100%); }
  .hook {
    position: absolute; top: 8%; left: 50%; transform: translate(-50%, 0);
    width: 90%; text-align: center;
    font-family: 'Anton', 'Impact', sans-serif;
    font-size: 8vw; /* or 8% of image width */
    font-weight: 400;
    line-height: 1.02;
    letter-spacing: -0.01em;
    text-transform: uppercase;
    color: white;
    text-shadow: 0 2px 6px rgba(0,0,0,0.45), 0 6px 24px rgba(0,0,0,0.35);
  }
</style>
<img class="bg" src="..." />
<div class="scrim"></div>
<div class="hook">HOOK TEXT HERE</div>
```

### Gallery (reproduce from scratch)
```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;800&display=swap" />
<style>
  body { position: relative; margin: 0;
    font-family: 'Inter', -apple-system, 'SF Pro Display', sans-serif;
    -webkit-font-smoothing: antialiased; }
  .bg { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; }
  .text-block {
    position: absolute; top: 10%; left: 8%;
    width: 62%; text-align: left; color: white;
  }
  .title {
    font-size: 6.5vw; /* or 6.5% of image width */
    font-weight: 700;
    line-height: 1.05;
    letter-spacing: -0.02em;
    margin-bottom: 0.35em;
  }
  .body {
    font-size: 3.3vw; /* or 3.3% of image width */
    font-weight: 400;
    line-height: 1.35;
    letter-spacing: -0.005em;
    opacity: 0.95;
  }
</style>
<img class="bg" src="..." />
<div class="text-block">
  <div class="title">Health</div>
  <div class="body">Health isn't just about the gym. It's also about sleep, good food, and managing your stress levels.</div>
</div>
```

---

## Why these exact specs (the research)

- **8% / 6.5% / 3.3% width-based sizing** → scales across all image resolutions.
  Tested on 480×600 and 1080×1350 — renders identically proportioned.
- **Anton for viral** → Google Fonts free, same visual weight as Impact but cleaner.
  Free, permissive license, easy CDN link.
- **Inter for gallery** → indistinguishable from Apple's SF Pro Display at a glance,
  but free and cross-platform. Most viral personal-brand accounts are using SF Pro
  or Inter — they're visually identical.
- **No shadow on gallery** → the personal-gallery image mode is designed with a
  dark empty zone; shadow would muddy it. Viral mode uses shadow because text
  often lands on any part of the image (uncontrolled).
- **Left alignment for gallery** → reference examples ("Health", "Traveling",
  "Tech Equipment") all use left. Feels editorial/personal. Center feels corporate.
- **62% width for body paragraph** → 2–3 line wrap is the sweet spot. Any wider
  and the text block fights the image.
