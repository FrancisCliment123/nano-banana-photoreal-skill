# nano-banana-photoreal

> Stop generating AI slop. Prompt engineering skill for photorealistic people in Google's Nano Banana (Gemini 2.5 / 3 Pro Flash Image).

A Claude Code / OpenClaude skill that fixes the two most common Nano Banana failures:

1. **Plastic-skin, doll-eyed, symmetric-face AI slop**
2. **Garbled text overlays** (like `"TIY ADMN FROM 0 AGAIN"` instead of `"DIY FROM 0 AGAIN"`)

Built for creators using Nano Banana to generate viral Instagram/TikTok hook images,
founder portraits, and lifestyle content that should look like real phone photos, not AI.

---

## The problem

Left to defaults, Nano Banana produces this:

- Too-smooth skin, HDR glow, waxy finish
- Symmetrical model-like faces
- Dead, doll-like eyes (no catchlight)
- Generic "modern cafe" / "minimalist space" backgrounds
- Any text in the image → garbled letters, misspellings, wrong numbers

Because the training data skews toward retouched editorial, stock photos, and
Instagram filter aesthetic.

---

## The fix (in one screen)

Every photorealistic-person prompt should have all 5 layers:

```
1. SUBJECT        → 28-year-old, lived-in clothes, ONE imperfection
2. ENVIRONMENT    → specific real place, 1-2 grounding props
3. CAMERA         → shot on iPhone 15 Pro, rear camera  (or 35mm f/1.8)
4. LIGHTING       → directional + time of day (never "natural light")
5. TEXTURE/GRAIN  → visible skin pores + cinematic catchlight in eyes
+ NEGATIVES       → Avoid: smooth skin filter, beauty retouch, ...
```

And for text:

```
Don't generate text in the image. Overlay it in post
(Canva / sharp / Puppeteer).
```

That's it. The skill files are the full playbook.

---

## What's in the box

```
SKILL.md                         ← Main entry, 5-layer algorithm + decision tree

templates/
  viral-hook-real-person.md      ← Instagram/TikTok hook images (the #1 use case)
  candid-phone-selfie.md         ← Amateur phone snapshot
  founder-working.md             ← Creator / SaaS founder portrait
  travel-candid.md               ← Outdoor lifestyle
  lifestyle-portrait.md          ← Editorial but authentic

reference/
  photorealism-core.md           ← The 5-layer algorithm, deep
  camera-tokens.md               ← Lens/camera tokens + what each does
  lighting-tokens.md             ← Directional lighting vocabulary
  skin-texture.md                ← Anti-plastic tokens
  negative-prompts.md            ← Copy-paste exclusion blocks
  text-rendering.md              ← The two-step method + code examples

examples/
  bad-vs-good.md                 ← Real prompt diagnoses (before/after)
  viral-hook-library.md          ← 15+ ready-to-adapt hook prompts
```

---

## Install

### As a Claude Code / OpenClaude skill

```bash
cd ~/.claude/skills
git clone https://github.com/FrancisCliment123/nano-banana-photoreal-skill nano-banana-photoreal
```

The skill registers automatically on next Claude session. Invoke with:

```
/nano-banana-photoreal
```

Or just mention Nano Banana / photorealistic / AI slop / viral hook image in a
conversation — Claude will pull the relevant reference file.

### As a reference

If you're not using Claude Code, you can use this as a standalone prompt
engineering playbook. Just read `SKILL.md` and pick the template that matches.

---

## Example — the ski-slope finance hook

**User's original bad prompt:**
```
A young investor standing in a cafe with the text "I'D START INVESTING LIKE THIS IF I
HAD TO DIY FROM 0 AGAIN" on top, for Instagram
```
Got: plastic-skin AI face + garbled text "TIY ADMN FROM 0 AGAIN".

**Fixed prompt:**
```
Candid iPhone photo of a 24-year-old man in a brown puffer jacket and white beanie,
standing on a snowy mountain terrace with ski lifts and fog in the background,
slight crooked smile, hands relaxed at sides. Overcast alpine light, soft diffusion,
no hard shadows. Shot on iPhone 15 Pro, rear camera, slight motion blur, visible
skin pores, peach fuzz on jaw, cinematic catchlight in eyes, slight asymmetry in
face. 9:16 aspect ratio. No text, no captions, no writing in the image.
Avoid: smooth skin filter, beauty retouch, plastic skin, airbrushed, symmetrical
face, HDR glow, AI aesthetic, stock photo feel, supermodel look.
```

Then overlay the hook text with Canva / Puppeteer / `sharp`.

Result: real-looking creator photo + pixel-perfect headline. Viral-ready.

---

## Credits

Built from synthesis of:

- [Google Cloud's official Nano Banana prompting guide](https://cloud.google.com/blog/products/ai-machine-learning/ultimate-prompting-guide-for-nano-banana)
- [Nano Banana 2 fal.ai technical guide](https://fal.ai/learn/tools/how-to-use-nano-banana-2)
- [Atlabs AI prompting framework](https://www.atlabs.ai/blog/nano-banana-2-prompting-guide)
- [CookedBanana's plastic skin fix methodology](https://www.cookedbanana.com/blog/fix-plastic-skin-ai-images-nano-banana)
- [Stockimg.ai advanced photorealism techniques](https://stockimg.ai/blog/prompts/advanced-prompt-techniques-getting-hyper-realistic-results-from-your-ai-photo-generator)

---

## License

MIT — use, modify, fork, whatever.

If you make something cool with it, [open an issue](https://github.com/FrancisCliment123/nano-banana-photoreal-skill/issues) or tag me.
