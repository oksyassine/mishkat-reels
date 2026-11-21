---
name: reel-motion-and-animation
description: "Use when designing or reviewing the motion and animation of an Islamic lecture reel: caption styles, title entrances, word emphasis, key lines, camera push and pull, verse and hadith panels, transitions, ambient effects, a library of looks drawn per reel, and deterministic frame-by-frame rendering (HTML canvas, Remotion, After Effects, ffmpeg). Most of it is taste; the hard limits are marked."
---

# Motion and animation

Motion serves his words. Most of this skill is **taste**: what worked for us, offered for you to improve. A few
**limits** follow from the principles and are not taste.

## Limits (not taste)

1. **Design never adds words.** Motion moves his words, the title, and attribution. It never writes new text, and a
   model choosing a look picks from a catalogue of values and word positions in his own words, nothing free-form.
2. **No playful motion on the Quran.** No glitch, shake, whip, bounce, scramble or "decrypt" on a verse; a quiet fade
   or a still panel. A transition that cuts to a flat colour fades instead over a verse.
3. **No emphasis on Allah's names** by word effects or emblems, and none on filler words («ما», «بعض», «ذلك»): emphasise
   meaning, not grammar.
4. **Nothing over his face** (see `reel-framing-and-layout`).
5. **Natural colours.** Motion may dim or vignette an outro; it never grades his picture.
6. **No music** and no sound bed under his voice.

## What worked for us (taste)

- **Calm by default.** A reel that came across as glitchy and distorted was traced to a strong zoom push-pull. A calm
  family (no glitch, shake, whip, handheld, crash zooms, info cards flying in) is our default; energetic families are
  opt-in.
- **More motion, gently.** Within the calm family we later chose to keep something always moving:
  captions mostly in motion (karaoke highlight, pill, underline, word-by-word reveal), a sweep or pen stroke on the
  title card, thin moment bars, and a slow camera push or pull of about 6 %.
- **Karaoke over a filled frame.** A "reveal" style that ghosts words across his clothes reads badly over a filled
  frame; a karaoke highlight on settled words does not.
- **One look per reel, drawn, not repeated.** Keep a library of looks grouped into families (calm, editorial, one-take,
  punchy). Per reel, draw one family and then one value per role (caption style, title entrance, backdrop, panel
  style), seeded by the item so a re-render reproduces it, and never the same value as the previous reel for the same
  role. Variety without chaos.
- **Key line.** Three to nine of his own words, shown large once, mid-frame, never during the title, moved below his
  face when the middle is his face, dropped if no size fits. His words, chosen, not written.
- **At most two callouts** a reel (a term, an ordinal «الأولى / الثانية», a contrast pair), placed off his face.
- **Verse panel** styles: a night panel with a small lamp, or a calm single line in a Quran font; the recited word
  lit lightly as he says it.
- **Opening a reply with a clip** (trend replies): the clip as a framed screen, its last frame held and greyed for
  about 0.7 s, then a short pixel dissolve into his reply, sound cross-faded and loudness matched. No bridge card.

## Engineering notes

- **Deterministic frames.** Render each frame as a pure function of time, with seeded randomness only.
  Then chunks can render in parallel, a re-render reproduces the look, and a preview at any second is exact.
- **Fonts.** Load every font before frame 0 and verify it reports loaded; a move that measures text in one face and
  draws it in another runs text out of its box. Use single-weight font aliases for moves that change weight.
- **Comments in templates.** An inline `//` comment in a minified one-line template swallowed the rest of the line and
  broke every frame. Preview a few seconds after every template change.
- **Composite once.** Draw the overlay on a transparent canvas and composite over the base video in one pass.
- **Previews.** Render stills at fixed moments (0.5 s, 3 s, 9.5 s, each panel, the outro) for every look change, on at
  least three reels: one filled, one whole-picture, one with a verse panel.

## Renderers

Everything here is renderer-agnostic. It has been done with an HTML canvas in headless Chromium composited by ffmpeg,
and it maps to Remotion (a React component per role, driven by `useCurrentFrame()`), After Effects (MOGRT templates with
the words as data), CapCut templates, or plain ffmpeg with `.ass` subtitles for captions. Ports and templates are very
welcome (see [CONTRIBUTING.md](../../CONTRIBUTING.md)).

## Checklist

- [ ] No word on screen that is not his, the title, or attribution.
- [ ] Verse panels enter quietly; no effect on Allah's names or fillers.
- [ ] Nothing over his face at any moment; stills checked at the fixed moments.
- [ ] Natural colours; no music.
- [ ] The look is recorded, so the reel can be re-rendered identically.
