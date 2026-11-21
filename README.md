# Mishkat Reels

**Open skills and recommendations for making faithful short vertical reels (Reels, Shorts, TikTok) from recorded
Islamic lectures.**

Short clips of scholars travel further than whole lectures ever will. They also travel without context: a sentence cut
in half, a verse written in the wrong riwaya, a caption that puts words in a scholar's mouth, a picture that should
never have been shown. This repository collects what we learned making such reels for
[Mishkat (مِشكاة)](https://mishkat.mssid.org/), an index of classical Arabic lectures, so that anyone doing the same
work can do it faithfully, and better than we did.

It is written for:

- **editors and volunteers** who cut lecture clips by hand, in any editor;
- **developers** building reel pipelines (ffmpeg, Remotion, After Effects, HTML canvas, anything);
- **AI agents** (Claude Code, or any agent that can read Markdown or connect to an MCP server);
- **channels and institutions** that publish their scholars' lectures and want clips made from them done right.

## The principles in short

Read [PRINCIPLES.md](PRINCIPLES.md) first. In one breath:

1. **His words, verbatim.** Captions are the speaker's own words from a checked transcript, word-timed. Light polish
   only (diacritics, punctuation).
2. **No machine-written words presented as his.** A title may summarise, but is never quoted or attributed to him and
   never carries a ruling.
3. **The Quran is never wrong.** Mushaf text only, only what he recited, in the riwaya he recites (never Hafs over
   Warsh), never sped up or cut inside.
4. **Hadith in his wording**, with no attribution or grade he did not give.
5. **Honest zero.** No good passage? Say so. A check that did not run has not passed.
6. **The sharia guard.** Standing alone, the reel must counsel, rule, warn or condemn. No music, no woman shown (not
   even blurred), no munkar presented neutrally, no fatwa framing.
7. **Truthful framing.** Never imply he commented on an event he did not address. Answer ideas, not people.
8. **Attribution.** Speaker, lecture title, and a link to the exact second of the original.
9. **A person decides what is published.** Every reel, every version, scheduled or not.

## Skills

Each skill is a folder with a `SKILL.md` (YAML frontmatter with `name` and `description`, then concrete steps and a
checklist). They are renderer-agnostic.

| Skill | Use it for |
|---|---|
| [reel-from-a-lecture-passage](skills/reel-from-a-lecture-passage/SKILL.md) | Start here: what a good reel is, lecture excerpts ("cards"), the order of work |
| [reel-cutting-on-sentences](skills/reel-cutting-on-sentences/SKILL.md) | Whole-sentence edges, word boundaries with air, trimming silences (never words), speed |
| [reel-verbatim-captions](skills/reel-verbatim-captions/SKILL.md) | Word-timed Arabic captions from the corrected transcript, rolling-caption repeats, title rules, sync check |
| [reel-quran-and-hadith](skills/reel-quran-and-hadith/SKILL.md) | Mushaf text in the reciter's riwaya, partial verses, false matches, hadith wording |
| [reel-sharia-guard](skills/reel-sharia-guard/SKILL.md) | The standalone test, pictures, sound, captions |
| [reel-framing-and-layout](skills/reel-framing-and-layout/SKILL.md) | 16:9 to 9:16, following the face, safe zones, title, colours, outro, cover |
| [reel-motion-and-animation](skills/reel-motion-and-animation/SKILL.md) | Motion taste, limits on verses, a library of looks, deterministic rendering |
| [reel-review-and-approval](skills/reel-review-and-approval/SKILL.md) | Layered checks, fail-closed reviews, human approval per version |
| [reel-edit-requests](skills/reel-edit-requests/SKILL.md) | Change only what was asked; versions; re-approval |
| [reel-answer-a-trend-or-statement](skills/reel-answer-a-trend-or-statement/SKILL.md) | Setting earlier teaching beside today's matters; statements answered claim by claim |
| [reel-outside-footage](skills/reel-outside-footage/SKILL.md) | Screening outside video shot by shot: picture, opaque cover or no picture, never a blur |
| [reel-with-ai-agents](skills/reel-with-ai-agents/SKILL.md) | The Mishkat MCP server, what an agent may and may not decide |

## Recommendations

Decisions taken while running a reel channel, each with the reason and the lesson behind it. They are ours. Borrow what
fits your audience.

- [Review and publishing](recommendations/review-and-publishing.md): a person reviews every reel, approval per
  version, fail-closed reviews, no automatic trend posts.
- [Passages, cuts and captions](recommendations/passages-cuts-and-captions.md): agree the passage before rendering,
  answer the matter itself, captions from the corrected transcript, silences trimmed never words.
- [Picture and motion](recommendations/picture-and-motion.md): fill the frame unless the face leaves the crop, never
  a blurred copy behind a moving camera, natural colours, calm motion.
- [Quran and hadith](recommendations/quran-and-hadith.md): no Hafs text over a Warsh recitation, no bulk verse changes.
- [Trends, statements and footage](recommendations/trends-statements-and-footage.md): settled matters only, quotes
  from the source, no name on screen, no woman shown.
- [Edits and agents](recommendations/edits-and-agents.md): an edit changes only what was asked; agents act, people
  approve.

## How to use the skills

**Just read them.** Each `SKILL.md` is a short handbook chapter with a checklist at the end.

**As Claude Code skills.** Copy or link the skill folders into your project's `.claude/skills/` (or your personal
`~/.claude/skills/`):

```
git clone <this repo> mishkat-reels
mkdir -p .claude/skills
cp -r mishkat-reels/skills/* .claude/skills/
```

**As a Claude Code plugin.** The repository carries `.claude-plugin/plugin.json`, so it loads as a plugin:

```
claude --plugin-dir ./mishkat-reels
```

**With other agents.** Any agent that supports the Agent Skills format (a folder with `SKILL.md` and `name` /
`description` frontmatter) can load them the same way; any other agent can be pointed at the files.

## The Mishkat MCP server

Mishkat runs a public, read-only [MCP](https://modelcontextprotocol.io/) server over its lectures, corrected
transcripts and verbatim excerpts:

- **URL:** `https://mishkat.mssid.org/api/mcp` (Streamable HTTP, no login)
- **About:** <https://mishkat.mssid.org/ai>

```
claude mcp add --transport http mishkat https://mishkat.mssid.org/api/mcp
```

For reels, two tools matter most:

- **`reel_guide`**: the full reel guide, consistent with this repository. Call it first.
- **`get_passage_words`**: every word of a passage (up to 180 s) with its second in the lecture, so cuts fall on whole
  sentences and captions are timed word by word.

Search tools (`search_treasures`, `search_lectures`, `find_verse_discussions`, `get_transcript` and more) find the
passage. See [reel-with-ai-agents](skills/reel-with-ai-agents/SKILL.md).

## Collaborate with us

This is a beginning, not a finished manual. We would be grateful for your help, and the reward of beneficial knowledge
shared is with Allah. Things we would love to receive:

- **Animations and motion templates**: caption styles, title entrances, verse panels, outros, transitions that stay
  calm and respectful. Ports to **Remotion**, **After Effects** (MOGRTs), **CapCut** templates, **ffmpeg/ASS** styles,
  **DaVinci Resolve** or **Premiere** presets.
- **Caption styles** for Arabic that stay legible over any background, and well-shaped right-to-left rendering
  recipes.
- **Rules and checklists**: a gap you found, a fault that slipped through, a better test. Anything touching the Quran,
  hadith or rulings is reviewed by a person of knowledge before it is merged.
- **Quran tooling**: riwaya-aware text and fonts (Warsh, Qalun, Duri and others), better verse detection, verse-edge
  trimming.
- **Measurements**: current safe zones from real phone screenshots of each app; loudness and readability tests.
- **Translations** of the skills and recommendations into other languages (Arabic first, then Urdu, Indonesian,
  Turkish, French, and more).
- **Other lecture sources**: notes on working with other scholars' archives, other languages, audio-only lectures.
- **Real examples**: before/after pairs that show a rule working.

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to propose something.

## Licence

The text of this repository is licensed under
[Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](LICENSE). Any code snippets in it are
also available under the [MIT licence](https://opensource.org/license/mit), so you can use them in your own tools
without restriction.

The lectures themselves belong to their speakers and channels. This repository contains no lecture content; follow
each channel's terms, and credit and link the original lecture in every reel.
