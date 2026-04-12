# Text Rendering — The Two-Step Method

**The single biggest rule of this skill:** do not generate text inside the image
with Nano Banana for anything longer than 5 words.

The user's second screenshot is the textbook case:
`"I'D START INVESTING LIKE THIS IF I HAD TIY ADMN FROM 0 AGAIN"`

That was supposed to be `"DIY AGAIN FROM 0"` but Nano Banana garbled it.
Even Nano Banana 2 (Gemini 3 Pro) still mis-renders multi-word text at
typical generation resolutions.

---

## The rule

| Text length | Strategy |
|---|---|
| 1–3 words, large, stylized | Nano Banana can handle it (sometimes) |
| 4–5 words | Risky, but attempt with quoted exact text |
| 6+ words | **ALWAYS** use the two-step method |
| Contains numbers or punctuation | **ALWAYS** two-step |
| Small text | **ALWAYS** two-step |

---

## The two-step method

### Step 1 — Generate a clean, text-free image

In your Nano Banana prompt, explicitly exclude text:

```
... 9:16 aspect ratio. No text, no captions, no writing in the image,
no watermark, no signs, no labels.
```

Add `no signs, no labels` if the scene contains things that could render as
text (store fronts, book covers, etc).

### Step 2 — Overlay the real text

Choose based on context:

---

## Option A — Canva (manual, 90 seconds)

1. Upload the generated photo as background
2. Add text frame, position in top third (Instagram hook standard)
3. Font: bold condensed sans-serif. Good picks:
   - **Impact** (classic viral)
   - **Bebas Neue** (cleaner, modern)
   - **Oswald** (slightly more rounded)
   - **Anton** (Bebas alternative)
4. Color: white with a soft drop shadow (3–6px blur, 50% opacity)
   — NOT a hard black outline, which looks dated
5. Line breaks: break after natural pauses, not mid-phrase
6. Size: readable at thumbnail (80–120px at 1080×1920)

---

## Option B — `sharp` + SVG (programmatic)

For autoposter pipelines. Already used in many Node-based image workflows.

```js
const sharp = require('sharp');

async function addHookText(inputPath, outputPath, hook) {
  // Split hook into lines of ~20 chars max
  const lines = wrapText(hook, 20);

  const svg = `
    <svg width="1080" height="1920" xmlns="http://www.w3.org/2000/svg">
      <style>
        .hook {
          font-family: 'Impact', 'Arial Narrow', sans-serif;
          font-weight: 900;
          font-size: 96px;
          fill: white;
          text-anchor: middle;
          paint-order: stroke;
          stroke: rgba(0,0,0,0.35);
          stroke-width: 2px;
        }
      </style>
      ${lines.map((line, i) =>
        `<text x="540" y="${280 + i * 110}" class="hook">${escapeXml(line)}</text>`
      ).join('\n')}
    </svg>
  `;

  await sharp(inputPath)
    .composite([{ input: Buffer.from(svg), top: 0, left: 0 }])
    .toFile(outputPath);
}

function wrapText(text, maxChars) {
  const words = text.split(' ');
  const lines = [];
  let current = '';
  for (const word of words) {
    if ((current + ' ' + word).length > maxChars) {
      lines.push(current);
      current = word;
    } else {
      current = current ? current + ' ' + word : word;
    }
  }
  if (current) lines.push(current);
  return lines;
}

function escapeXml(s) {
  return s.replace(/[<>&'"]/g, c => ({
    '<':'&lt;','>':'&gt;','&':'&amp;',"'":'&apos;','"':'&quot;'
  })[c]);
}

// Usage
addHookText(
  'generated.jpg',
  'final.jpg',
  'HOW TO START INVESTING STEP BY STEP'
);
```

---

## Option C — Puppeteer HTML → PNG (full creative control)

For when you want exact web-grade typography, curved text, gradients, etc.

```js
const puppeteer = require('puppeteer');

async function renderHookImage(bgPath, hook, outPath) {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.setViewport({ width: 1080, height: 1920 });

  const html = `
    <!doctype html>
    <html><head><style>
      @import url('https://fonts.googleapis.com/css2?family=Anton&display=swap');
      * { margin: 0; padding: 0; box-sizing: border-box; }
      body {
        width: 1080px; height: 1920px;
        background: url('file://${bgPath.replace(/\\/g, '/')}') center/cover;
        position: relative;
        font-family: 'Anton', 'Impact', sans-serif;
      }
      .hook {
        position: absolute;
        top: 12%;
        left: 50%;
        transform: translateX(-50%);
        text-align: center;
        color: white;
        font-size: 96px;
        font-weight: 400;
        line-height: 1.05;
        letter-spacing: -0.01em;
        text-shadow: 0 4px 16px rgba(0,0,0,0.4);
        width: 90%;
        text-transform: uppercase;
      }
      .subhook {
        position: absolute;
        top: 36%;
        left: 50%;
        transform: translateX(-50%);
        text-align: center;
        color: white;
        font-size: 44px;
        font-weight: 400;
        text-shadow: 0 2px 8px rgba(0,0,0,0.5);
        width: 80%;
      }
    </style></head><body>
      <div class="hook">${escapeHtml(hook.main)}</div>
      ${hook.sub ? `<div class="subhook">${escapeHtml(hook.sub)}</div>` : ''}
    </body></html>`;

  await page.setContent(html);
  await page.screenshot({ path: outPath, type: 'png' });
  await browser.close();
}
```

This matches the exact viral-post aesthetic: big condensed uppercase main hook,
smaller subtitle underneath, both with soft drop shadow.

---

## If you must generate text in the image

(Rare, small-stakes cases only.)

### Rules for embedded text
1. **Use quotation marks** for the exact string: `with text "EARN MORE"`
2. **Max 3–5 words**
3. **No numbers** (Nano Banana mangles digits especially hard)
4. **Large size** (generate at 2K+ resolution; small text never survives)
5. **Simple font** — specify something common: `bold sans-serif font`
6. **Single language** — no mixing

### Example (embedded text attempt)
```
... minimalist white card with the text "START HERE" in bold black sans-serif,
centered, large font size. 2K resolution.
```

Even this fails ~30% of the time. That's why two-step is the default.

---

## Summary

```
Will your image have text?
│
├── NO  → Just prompt normally, exclude text in the prompt
│
└── YES
    │
    ├── ≤ 3 words, large, stylized → Try embedded, have fallback
    │
    └── Anything else → TWO-STEP METHOD
        1. Generate clean image (no text)
        2. Overlay text in post (Canva / sharp / Puppeteer)
```
