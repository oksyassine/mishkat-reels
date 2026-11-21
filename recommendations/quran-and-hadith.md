# Quran and hadith

## No Hafs text over a Warsh recitation

**Recommendation.** Know the riwaya each speaker recites in, and show verses in that riwaya's mushaf text (for example
the KFGQPC Warsh text and font for Warsh). If you do not have it, show no verse text; his recitation stays as sound.

**Why.** The letters differ between riwayat in many places. A viewer who knows the Quran sees a mismatch between what
is heard and what is written: on the Quran, that is an error, not a style.

**Lesson.** Our verse panels were built for Hafs, which most texts and APIs provide. When channels that recite in Warsh
were added, their lecture reels could show Hafs text over a Warsh recitation. Warsh text and a Warsh font were added
to the renderer, and the rule became: no verse panel at all for a reciter whose riwaya text you do not have.

## Only the mushaf text, only what he recited

**Recommendation.** Draw verses from the mushaf text, never from the transcript, and only the words he actually
recited. A partial verse is shown as partial, with its reference.

**Lesson.** Several false matches taught us to be strict: the isti'adha matched as a verse, a basmala glued to a
surah's first verse, a common formula about the Prophet ﷺ matched part of a verse, and a well-known hadith matched a
verse it echoes. Each now has its own guard (see the `reel-quran-and-hadith` skill).

## No bulk changes to verse text

**Recommendation.** Fix verses in a transcript fragment by fragment, each one heard and reviewed by a person.

**Lesson.** An early tool replaced whole caption cues of speech with whole verses, overwriting the scholar's own
words around them. The tool was retired; verse fixes are now fragment-level, heard and reviewed.

## Never speed or cut a recitation

**Recommendation.** A recited verse, with a margin around it, plays at 1.0x and is never trimmed, whatever the reel's
speed or silence trimming.

## Quiet presentation for verses

**Recommendation.** No glitch, shake or playful entrance on a verse panel.

## A hadith in his words, without added attribution or grade

**Recommendation.** Show a hadith as he said it, under a neutral label («في الحديث»), never «قال النبي ﷺ» on your own,
and with no grade he did not state. If a panel turns out to show his paraphrase, switch the panel off and keep the
words as captions.

**Lesson.** A hadith panel once showed the speaker's paraphrase as if it were the text. A reviewer caught it; the
remedy is to turn the panel off, not to hold the whole reel.
