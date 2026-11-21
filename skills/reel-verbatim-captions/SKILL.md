---
name: reel-verbatim-captions
description: "Use when making or fixing the on-screen Arabic captions of a lecture reel: verbatim words from the corrected transcript, per-word timing, captions that are late, early, doubled or missing a line, rolling auto-subtitle repeats, a lecture with no word timings, the title line rules, legibility, and a sync check that proves the captions follow his voice."
---

# Verbatim, word-timed captions

The captions are his words, each lit at the moment he says it. Two faults are invisible to anyone checking stills:
**time** (a word shown seconds before or after it is heard) and **text** (a word shown twice, a line missing, a verse
in transcript spelling). Both must be checked by measurement or by ear.

## Rules

1. **Text from the corrected transcript, not the auto-subtitles.** Auto-captions are raw speech recognition; repairs
   made to the transcript (a restored verse, a corrected name, a removed hallucination) never reach a reel that
   reads the subtitle file directly. Read the transcript you corrected.
2. **His words, in his order, nothing added.** No paraphrase, no shortening inside a sentence, no model retyping.
   Allowed: diacritics and punctuation, nothing else. Two narrow, display-only cases we treat as part of that polish,
   because they change marks and not words: the hamza or madda a transcript left out of an unambiguous word (القرآن
   for «القران», الأطفال for «الاطفال»), and the sign ﷺ drawn for the spoken «صلى الله عليه وسلم». Never touch an
   ambiguous form (ان، امه، سنه): you cannot know which reading he meant from the letters alone.
3. **Listen.** The transcript is a machine transcription corrected in places. If what you hear differs from the text,
   repair the transcript (with the audio as the stated source) or choose another passage.
4. **Show a phrase twice only if he said it twice.**
5. **Verses and hadith** follow `reel-quran-and-hadith`: a verse is never drawn from transcript text.

## Where word times come from (best first)

1. **Forced alignment** of the transcript to the audio (for example WhisperX or another aligner): measured.
2. **A transcription engine that returns word times** for the clip itself: measured, for that clip.
3. **The video platform's own per-word tags** in automatic subtitles (YouTube's rolling captions carry `<c>` word
   tags with times): measured, if matched to your transcript **by text**, not by time.
4. **Letter-count estimate:** each word gets a share of its segment's window in proportion to its length. Use only as
   a last resort, and mark the reel.

Why the estimate fails: rolling auto-captions show a line when the **next** line starts, so a segment's window can lag
the speech by a whole line (we measured up to 5–7 s). Estimated words inherit the lag, and a silence cutter that
trusts them cuts over speech.

Aligning your corrected tokens to the timed raw words: normalise letters (strip diacritics, fold hamza forms, ى/ي,
ة/ه), align with a diff, copy times for equal words, split a replaced span by letter length, and spread unmatched
tokens between their neighbours. Ignore timed words whose middle falls well outside the segment's window. If under
about 40 % of a segment's tokens match, treat the whole segment as estimated.

## Rolling-caption repeats

Captions built from rolling auto-subtitles often repeat the last words of one segment at the start of the next.
Example: «… قبل المعالم الجزئيه» ending one line and «قبل المعالم الجزئيه …» opening the next, said once. A plain
one-word line in the subtitle file (often a single word such as a surah name) is easy to skip by mistake when parsing,
which then creates a missing word or a false double.

To fix: align the segment tokens to the subtitle file's own word stream; at each join where the same run ends one
segment and starts the next, drop the copy the stream does not carry. Do it as a reviewed repair, list the cases you
cannot decide (both copies or neither match), and never let a fix empty a segment.

## The title line

A short title may summarise (an excerpt's index summary is a good start), but it is not his words:

- never in quotation marks, never attributed to him, never carrying a ruling (حرام، يجوز، بدعة …);
- never cut off on screen: step the size down until it fits in at most three lines, measured in the font it is
  actually drawn in;
- shown briefly at the start, never over his face.

## Legibility

- Arabic font with full diacritics (for example Amiri or Noto Naskh Arabic); right-to-left shaping (libass built with
  HarfBuzz, or an editor that shapes Arabic). Check a rendered frame: joined letters, marks in place, word order.
- A soft dark band (scrim) under the caption lines whenever the picture reaches them. White words vanish on a white
  robe.
- Group words into phrases that break on pauses and sentence ends; at most two lines; inside the safe zones
  (`reel-framing-and-layout`).
- No emoji in lecture names on screen (they render as empty squares in many fonts); keycap digits become plain digits.
- Non-Arabic speech in a clip, when allowed, is captioned left to right in its own language, from its own words, never
  translated on screen.

## Sync check (measure, do not eyeball)

What worked for us on the finished file (after any retime, mapping caption times through the retime):

| Fault | Rule of thumb |
|---|---|
| estimated | a segment of the cut has no measured word times |
| repeated | the last 1–6 words of one segment equal the first words of the next on screen, and the audio has them once |
| uncaptioned | over about 1.2 s of sound clearly above the pause level with no caption word within ±0.25 s |
| late / early | after each pause over about 0.35 s, compare the next caption word with the nearest voice onset (within ±0.8 s); fault when the median offset exceeds about 0.25 s |

By hand: `ffmpeg -i reel.mp4 -af silencedetect=noise=-35dB:d=0.3 -f null - 2>&1 | grep silence_end`, then compare
each `silence_end` with the first caption word after it, and look at three such moments as stills with the lit word.

A sync fault holds the reel before any visual review. Reviewers who look at stills cannot hear.

## Checklist

- [ ] Caption text equals the corrected transcript of the cut (only diacritics, punctuation, missing hamza or madda
      on unambiguous words, and ﷺ differ).
- [ ] Every segment has measured word times, or the reel is marked estimated.
- [ ] No doubled phrase he said once; no missing line.
- [ ] Onsets after pauses within about ±0.25 s.
- [ ] Title: no quotes, no attribution, no ruling, whole on screen, off his face.
- [ ] A rendered frame read by an Arabic reader: shaping, marks and order correct.
