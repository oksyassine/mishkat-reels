---
name: reel-review-and-approval
description: "Use when checking a finished lecture reel before it is published, or designing the review steps of a reel pipeline: mechanical checks (edges, loudness, safe zones), the caption sync check, the visual review, the scholarly review of the cut and its meaning, human approval before publishing (scheduled reels included), versions and re-approval, and why a review that did not run is never a pass."
---

# Review and approval

Every reel is reviewed in layers, cheapest first, and then approved by the person responsible before it is published.
Each layer catches what the others cannot: stills cannot show timing; a model cannot hear; a meter cannot judge
meaning.

## Hard rules

1. **A review that did not run is never a pass.** If any check errors, times out, runs out of quota or returns
   nothing, the reel is held. Make your pipeline raise on a missing answer rather than read "no faults found". We
   learned this when a whole batch of reels went forward as "passed" while every review call was being refused.
2. **A person approves every reel before it is published**, scheduled ones included. Send a scheduled reel to them
   well ahead of its time (we use 48 h); without approval at its time, it is held and sent again, not posted.
3. **An approval covers the version that was watched.** A re-made or edited reel needs a new approval. Every replaced
   version is marked so it can no longer be published. The caption approved is the caption posted: tie the approval
   to a fingerprint of the caption text and refuse it if the caption changed since.
4. **Fix by re-making, not by patching the file.** A fix goes back through the same steps and the same checks.
5. **Never loosen a threshold to make a reel pass.** Test any change to a check on a few known-good and known-bad reels
   first.
6. **Publish the full-size file.** A compressed preview sent for review is never the file that is posted.

## The layers (what worked for us)

### 1. Mechanical (free, local, run on every reel)

- **Edges:** loudness of the first and last ~0.12 s against the clip's speech level (70th percentile of 0.25 s
  windows); above about 0.45 of it suggests a cut mid-word. A cut placed exactly on a word onset is loud but clean.
- **Loudness:** integrated level near −14 LUFS (flag outside about ±3.5); a jump over ~10 LU between neighbouring
  voiced half-seconds (render seams); a quiet opening (first seconds more than ~12 LU under the whole).
- **Safe zones:** every drawn text box over time against the zones in `reel-framing-and-layout`.
- **Contact sheet:** six frames tiled, for a human look.

### 2. Caption sync (free, local)

The sync check in `reel-verbatim-captions`: estimated timings, repeated runs, uncaptioned speech, late or early
onsets. A sync fault holds the reel before any visual review.

### 3. Visual review (a model or a person)

About a dozen full-size frames, each labelled with what the renderer drew at that moment (so a lit karaoke word is
not mistaken for a chosen keyword, and a see-through title card by design is not called a fault). Look for: unreadable
text, text cut off, overlaps, anything over his face, broken rendering. Sample the title only after it has finished
entering.

### 4. Scholarly review (a person, or your most careful model with a person's final word)

Separate questions, each answered on its own:

- **Cut:** do the first and last words open and close a sentence? Show the reviewer numbered parts of the transcript
  around the cut and ask for the edges as words, then place them in the word times.
- **Meaning:** read with its context, does the clip say what he meant? Any munkar presented neutrally? Any verse or
  hadith panel showing a paraphrase (switch that panel off rather than hold the whole reel)?
- **Framing:** should it be filled? Does the window stay on his face?
- **Screen:** is anything over his face, cut off, unreadable?

A reviewer's answer to "widen the cut" can flip between runs: compare against the cut that actually played, and cap
the number of fix rounds (we use two) before holding the reel for a person.

### 5. The person responsible

Watch the whole reel with sound, read the caption, then approve, ask for one change, or drop it. Watching matters:
stills cannot show timing.

## Make only what is needed

- Do not render reels nobody asked for. A reel answering a trend is made only after the passage was agreed.
- Make a scheduled reel close to its day (we use within 3 days), so a fix to the pipeline reaches it and nothing is
  made twice.
- Do not spend real reviews or renders just to "test" a check; run the free local checks on existing files.

## Checklist

- [ ] Every check actually ran and returned a real answer.
- [ ] Mechanical: edges, loudness, zones clean (or accepted design notes only).
- [ ] Sync: measured timings, no repeats, no uncaptioned speech, onsets within about ±0.25 s.
- [ ] Visual: nothing over his face, nothing cut off.
- [ ] Scholarly: cut on sentences; meaning faithful; panels show mushaf text and his own words.
- [ ] Watched with sound and caption read by the person responsible; their approval tied to this version and this
      caption.
- [ ] Older versions marked as replaced.
