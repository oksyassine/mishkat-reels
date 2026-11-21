---
name: reel-cutting-on-sentences
description: "Use when setting or fixing the start and end of a reel cut from a lecture: cutting on whole sentences, placing edges between words with a little air, a reel that ends on a sentence only started or opens on a stray word, a clipped first or last syllable, trimming silences without losing words, choosing playback speed, and never cutting or speeding a Quran recitation."
---

# Cutting on whole sentences

A cut that starts or stops in the wrong place changes what he said. It is the most common fault in lecture reels and
the easiest to miss on stills. Settle the cut **before** you fetch or render anything.

## Rules

1. **Whole sentences.** Start on the first word of a sentence and end on the last word of one. Never start or end
   mid-sentence, and never end on the first words of the next hadith, verse or matter.
2. **Widen, never shrink, an excerpt.** If a pre-picked excerpt stops inside a sentence, widen to the nearest
   sentence edge without dropping any part of it, and keep the total at 90 s or less. If that is impossible, choose
   another passage.
3. **Trim silences only, never words.** A pause is shortened only where the gap between words is longer than about
   half a second **and** the audio itself is quiet there. Keep a little pause on each side.
4. **Speed.** Normal speed, or at most a mild speed-up (around 1.1x). Never speed up, slow down or cut inside a Quran
   recitation: the verse plays as he recited it.
5. **One voice.** In many transcripts `>>` (or a similar mark) means a change of speaker: check the audio around it.

## Placing an edge

1. Find the sentence edge in the transcript (punctuation is unreliable in machine transcripts: read for meaning).
2. Take the word times of the first and last words.
3. Place each edge in the gap between words: about **0.2–0.4 s** before the first word starts and after the last word
   ends, at the quietest point there. Never on the previous word's tail, never on the next word's onset.
4. A word belongs to the cut by its middle. If the last word's middle lies past your end, the word is either fully in
   or fully out: decide, do not split it.
5. Check how the word times were made. When they are **measured** (forced alignment, or a source's own per-word
   tags), trust them to about a tenth of a second. When they are **estimated** (a segment's time shared out by
   letter count), they can lag the speech by seconds: find the true edges by ear or on a waveform.
6. Word times are lecture seconds. Subtract your section's start, and remap captions after any trim or speed change.

## Trimming silences safely

The tempting shortcut is to cut wherever the word list shows a gap. That fails: an aligner sometimes squeezes words
into a few tens of milliseconds and leaves a "gap" that lies over speech. A cutter that trusts that gap removes words.
In practice this once silently removed «أظلم الظلم» from a passage that went on from «ومن أظلم».

Do both checks:

1. The word gap is over about 0.5 s.
2. The audio is quiet across the gap. For example, `ffmpeg -af silencedetect` with a threshold set relative to the
   clip's own mean level (we use about 18 dB under the mean, clamped to a sensible range), minimum duration about
   0.25 s.

Cut only where both agree, and leave about 0.15 s of pause on each side. Exclude these spans from any cut or speed
change: a recited verse with a margin of about a second around it, the first seconds while the title is read, and
any held final frame.

## Speed

A mild speed-up (about 1.1x) keeps attention without changing his voice. If you vary it, derive it from the
speaker's own pace (a slow speaker tolerates more). Keep recitation at 1.0x. When re-making an older reel, keep the
speed it was made at unless asked (see `reel-edit-requests`).

## Checklist

- [ ] Read the first and last words: the reel opens a sentence and closes one.
- [ ] **Listen** to the first and last second: no clipped syllable, no word of the next sentence.
- [ ] Word times were measured, or the edges were found by ear.
- [ ] Every trimmed pause lies over quiet audio; no word of his is missing (compare the captions with the transcript).
- [ ] No cut or speed change inside a recitation.
- [ ] Total 20–90 s after the retime.
