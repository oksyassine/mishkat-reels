---
name: reel-quran-and-hadith
description: "Use when a reel contains a recited Quran verse or a hadith: showing the verse in the mushaf text of the reciter's riwaya (never Hafs over Warsh), partial verses and references, false verse matches (isti'adha, basmala, formulas), never cutting or speeding a recitation, verse animation limits, and showing a hadith in the speaker's own wording without added attribution or grade."
---

# Quran and hadith on screen

This is the part of a reel that must never be wrong. When in doubt, show less: his recitation stays as sound, his
words stay as plain captions.

## Quran: rules

1. **Mushaf text only.** A recited verse is shown in the canonical text of the mushaf, exactly as printed there. Never
   draw transcript or recogniser text as Quran, and never retype a verse.
2. **Only what he recited.** Show exactly the run of words he recited. If he recited part of a verse, show that part
   with its reference (surah and verse) and do not present it as the whole verse. One way that works: show the
   reference badge only when the run reaches the verse's end; otherwise mark it as part of the verse.
3. **The riwaya he recites in.** Many reciters (for example across North and West Africa) recite in Warsh; most
   printed texts and APIs give Hafs. The letters differ in places. **Never lay Hafs text over a Warsh recitation.** Use
   that riwaya's mushaf text (for example the KFGQPC Warsh text and font), or show no verse text.
4. **Certainty or nothing.** If you cannot identify the verse with certainty, show no verse text over the recitation.
5. **Never cut or speed a recitation.** It plays at 1.0x with a margin of about a second around it, whatever the
   reel's speed. If a cut would open mid-verse, move it to the verse's first recited word or out of the verse.
6. **Quiet presentation.** No glitch, shake, whip, bounce or playful entrance on a verse; a calm fade or a still panel.
   Never draw a verse in a decorative caption style meant for his speech.
7. **No bulk changes.** A fix to verse text in a transcript is made fragment by fragment, heard and reviewed by a
   person. Never replace whole caption cues of speech with whole verses: that overwrites his commentary.

## Finding the verse (and the traps)

Use a reference source when you have one (an index that already maps the passage to surah and verse, such as the
Mishkat tools' verse lookup). Otherwise match his words against the whole Quran, and guard against these false
matches, each of which we have seen:

- **The isti'adha.** «أعوذ بالله من الشيطان الرجيم» matches a verse (16:98) but is not a recitation of it. Skip the run
  after «أعوذ» / «نعوذ».
- **The basmala** said before a surah's first verse glues onto that verse in a match, and a basmala alone has been
  matched to an unrelated verse. Treat it separately from the verse.
- **Formulas.** «عن رسول الله» has matched part of a verse. Require several matched words beyond common formulas (we
  use at least 3–4 strong words).
- **Hadith that echo verses.** The hadith of Jibril («… بالله وملائكته وكتبه ورسله واليوم الآخر … والقدر») matches 4:136.
  A hadith cue around the words («قال ﷺ», «في الحديث») should block a Quran-wide match.
- **A run found in two verses** has no single reference: show it without a reference or not at all.
- A cue before the run («قال تعالى», «قال الله») or a verse edge raises confidence; its absence lowers it.

## Fonts and rendering

- A Quran font for verses (for example Amiri Quran or the KFGQPC Uthmanic fonts), separate from the caption font.
- Check a rendered frame of every verse: every mark in place, no broken ligature, nothing clipped at the panel edge.
- While a verse is shown in its panel, his transcript words of that verse leave the captions, so nothing is drawn twice.

## Hadith

1. **His wording.** Show the hadith as he said it. If a written excerpt exists, use it only to locate the span, then
   show his spoken words.
2. **No attribution of your own.** Do not label it «قال النبي ﷺ»: he may be quoting a companion or a narrator, or
   paraphrasing. A neutral label («في الحديث») over his words is safer.
3. **No grade** he did not state.
4. **A paraphrase is not a hadith panel.** If a reviewer finds that a "hadith" panel shows his paraphrase, switch the
   panel off; the words stay as ordinary captions.

## Checklist

- [ ] Every verse panel's words compared with the mushaf (surah, verse) **and** with what he recites (listen).
- [ ] The riwaya of the recitation is known, and the text matches it; otherwise no verse text.
- [ ] Partial verse shown as partial; reference correct.
- [ ] No cut or speed change inside a recitation; no playful motion on a verse.
- [ ] No isti'adha, basmala, formula or hadith matched as a verse.
- [ ] Every hadith panel shows his words; no added «قال النبي ﷺ», no added grade.
- [ ] Any verse fix in the transcript was heard and reviewed by a person.
