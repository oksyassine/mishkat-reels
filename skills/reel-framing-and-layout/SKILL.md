---
name: reel-framing-and-layout
description: "Use when turning a 16:9 lecture picture into a 9:16 reel and placing what is drawn over it: fill the frame vs keep the whole picture, a crop window that follows the speaker's face, never a blurred copy behind a moving camera, interviews, nothing over the face, title box fit, app safe zones, natural colours, loudness, the outro and the cover image."
---

# Framing and layout

How the lecture's wide picture becomes a vertical reel, and where text may go. The rules marked **rule** come from
decisions that held up in practice; the ones marked **taste** are choices you may change.

## Format

- 9:16, **1080x1920**, at the source's own frame rate (a 25 fps lecture drawn at 30 fps judders).
- Loudness around **−14 LUFS** integrated; no quiet opening; no clipped first or last syllable.
- Encode as few times as you can: each lossy pass softens his face and the text.

## Framing the picture

1. **Rule: fill the frame with him** whenever his face stays inside a 9:16 crop of the picture in every frame of the
   cut (allow a little slack, about a fifth of a face width). Filled reels read better on a phone, and in our
   experience they are the ones that get watched.
2. **Rule: let the window follow his face** when he moves (leans, walks, the camera reframes). Keep the window still
   while his eyes, nose and mouth stay inside it with some room; ease it across slowly (over 1–3 s) when he moves;
   jump on the very frame of a camera cut, never pan across a cut; never let it leave his face. Track the facial
   landmarks, not the centre of the face box: a lean can push the box centre inside while the face is cut at the edge.
3. **Rule: keep the whole picture** when no window can hold him: two people in an interview, his face unseen for
   seconds, a wide moving shot, another person's face jumping into place. If he only sways within a band, crop the
   sides to where his head moves (plus a margin) so the picture is taller.
4. **Rule: never a blurred copy of a moving camera behind the picture.** When the whole picture is kept and the camera
   moves, the background is plain, a still texture or a gradient. A blurred, moving copy of the same shot behind it
   is distracting and looks like a mistake. Over a still camera a darkened blur is acceptable (taste).
5. A face detector is enough to decide (for example YuNet in OpenCV): sample about 48 frames across the cut, count
   frames where the face leaves the 9:16 band, and look for a second large face. Faces in profile or small in a wide
   hall may be missed: fall back to keeping the whole picture.

## Nothing over his face

- **Rule:** the title, captions, key lines, callouts, number badges and any decoration stay off his face. Measure the
  face band (top, bottom, eye line) and place things around it: the title ends above his eyes (with about 40 px to
  spare), callouts move below the face or just above the captions, a number badge never sits between his eyes.
- When there is no room in a tight close-up, drop the decoration. His words stay as captions.

## Safe zones (approximate, not official)

Short-video apps draw their own interface over the reel. Figures that work for 1080x1920:

| Zone | Keep text out of |
|---|---|
| top | 0–150 px (better 175–200) |
| bottom | 1620–1920 px hard; treat 1500–1620 with care; captions sit above about y 1440 |
| sides | about 130 px each |
| right button column | x 950–1080, y 1100–1750 |

Check every drawn text box over time, not only on one frame: a box that stays in a hard zone for more than about
0.75 s is a fault. Measuring the current interface on a real phone screenshot is a welcome contribution.

## Title

- Whole on screen, never cut: step the size down until it fits in at most three lines, measured in the font it is
  actually drawn in (a font that loads late measures wrong).
- **Taste that worked for us:** a see-through card for the first ~10 s only, then gone; or bold words on a dark
  fall-off. Not over his face.
- If a verse panel opens the reel, decide where the title goes before rendering; do not let one hide the other.

## Colours

- **Rule: natural colours.** No grading, no film look, no grain, no light leaks, no filters on his picture. A "vintage"
  skin once turned a reel sepia; grain also multiplied file size several times.

## Outro

**Taste:** hold the last frame (about 3 s) after his voice has ended, dimmed, with his name, the lecture title, and a
link or QR code to the exact second of the original. Any numbers shown must be real (the lecture's length, where the
clip sits in it). Keep the outro uncluttered: one card, nothing overlapping.

## Cover image

- Choose the best frame, not any frame: his face found, large, near the middle, sharp (for example the variance of the
  Laplacian), eyes open, calm, facing the viewer.
- Any title on the cover sits low (on his chest), never on his face, readable at thumbnail size.

## Checklist

- [ ] Filled when his face stays in the crop; window follows his face; whole picture for interviews.
- [ ] No blurred moving copy behind a moving camera.
- [ ] Stills at: title entering, title settled, title leaving, each callout and key line, each verse panel, a camera
      cut in a tracked shot, the last caption, the outro, and the cover at thumbnail size.
- [ ] Nothing over his face; nothing in a hard safe zone for more than about 0.75 s.
- [ ] A base frame compared with the source at the same second: identical tones.
- [ ] Loudness near −14 LUFS; first and last syllables whole.
