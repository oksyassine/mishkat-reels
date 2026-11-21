# Review and publishing

Decisions taken while running a reel channel from lectures, written as recommendations. Each one has the reason and
the lesson behind it.

## A person reviews every reel before it is published, scheduled ones included

**Recommendation.** Nothing reaches a public account until the person responsible has watched it with sound and read
its caption. A scheduled reel is sent to them well ahead of its time (we use 48 hours). If its time comes without
their approval, it is held and sent again, not posted.

**Why.** Automatic checks catch a lot, but not everything: late captions, a word said once and shown twice, a cut that
changes the meaning. A schedule is a promise of a time, not a review.

**Lesson.** A reel that had passed every automated review, and was already scheduled, turned out to show words twice
and to have captions that lagged the voice. Watching it caught that before its time came. Since then, scheduling and
approval are separate steps, and approval is always explicit.

## An approval covers one version

**Recommendation.** Tie every approval to the exact version and caption that were watched (for example a fingerprint of
the caption text). A re-made reel, or a changed caption, needs a new approval. Mark every replaced version so it can
never be published.

**Why.** Pipelines re-make reels to fix faults. If the old approval carries over, the person ends up approving
something they never saw.

**Lesson.** An approval given to one version was about to apply to a newer one the pipeline had re-made twice. The
approval was not carried over; the current version was sent for its own.

## A review that did not run is never a pass

**Recommendation.** Every check must return a real answer. An error, a time-out, a usage limit or an empty response
holds the reel.

**Why.** The easy code path reads "no faults reported" as "passed".

**Lesson.** When review calls were refused for a while, a whole batch was marked as passed and sent forward for
approval. Nothing was posted, because a person still had to approve, but the safety net had silently gone. Now a
missing answer raises an error and stops the run.

## No automatic trend reels, no automatic posts

**Recommendation.** Do not let a schedule render or publish replies to trends on its own. A trend reel is made only
after the person responsible agreed to its passage, and posted only on their word.

**Why.** Matching a passage to a current event is a judgement about the scholar's words and about today's world. Done
automatically, it produces reels nobody asked for, some on matters that needed a human eye.

**Lesson.** An automatic step that matched excerpts to the day's trends began producing reels unasked. It was removed:
the daily process now only proposes.

## Make reels only when they are needed

**Recommendation.** Render a planned reel close to its day (we use within three days), not a month ahead.

**Why.** Every render and review takes time and effort, and pipeline fixes made in between would not reach reels made
early. Reels made far ahead also pile up versions to track.

## Publish the full-size file

**Recommendation.** The compressed preview sent to a phone for review is never the file that is posted.

**Why.** Previews are made small to fit messaging limits. Posting one loses quality permanently.

## Read the record before answering "why was this posted?"

**Recommendation.** Keep a log of every approval and post (who, when, which version, which caption), and answer from
it. Never guess.
