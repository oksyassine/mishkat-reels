# Contributing

Thank you for wanting to help. Every contribution here ends up shaping how a scholar's words reach strangers, so we
review carefully, and we are grateful for your patience.

## What you can propose

| Kind | Where it goes |
|---|---|
| A new skill (how to do a task: steps, rules, checks) | `skills/<skill-name>/SKILL.md` |
| A fix or addition to an existing skill | that skill's `SKILL.md` |
| A recommendation (a decision that worked, with its reason and lesson) | `recommendations/<area>.md` |
| An animation, motion template, caption style or renderer port | a pull request with the files, a short description, and a still or short preview |
| A translation | `translations/<language-code>/…`, mirroring the English file names |
| A question, an idea, a fault you saw | an issue |

## Writing a skill

- Folder name in kebab-case. `SKILL.md` starts with frontmatter whose `name` equals the folder name:

  ```
  ---
  name: reel-something
  description: "Use when … (name the concrete requests and situations that should trigger it)"
  ---
  ```

  Quote the description if it contains a colon or Arabic quotation marks.
- Hard rules first, then steps, then a checklist a person or an agent can actually tick.
- Concrete and testable: numbers that worked, commands, what to look at. Mark taste as **taste**.
- Renderer-agnostic where you can. Tool-specific recipes are welcome in their own section.
- English, with Arabic examples where they help. Latin digits (0123456789). No emojis.
- Do not invent rules: say where a rule comes from (a principle, a measured fault, a scholar's guidance).

## What every contribution must keep

Read [PRINCIPLES.md](PRINCIPLES.md). A contribution may refine how the principles are applied; it may not weaken them.
In particular:

- nothing on screen presented as the speaker's words that he did not say;
- verses only from the mushaf, in the reciter's riwaya, never sped up or cut inside;
- hadith in the speaker's wording, no added attribution or grade;
- the sharia guard: no music, no woman shown (not even blurred), no munkar presented neutrally;
- a person approves before anything is published;
- attribution and a link to the original in every reel.

An animation that is beautiful but places text on a speaker's face, adds a playful effect to a verse, or needs a
music bed will not be merged as a default. It may be welcome with those parts removed.

## Review by a person of knowledge

Anything touching the **Quran, hadith or rulings** (verse detection, riwaya handling, hadith presentation, what counts
as munkar, how a trend may be answered) is reviewed by a person with the knowledge to judge it before it is merged.
Please say in your pull request which parts touch these, and on what you base them.

## Examples of welcome contributions

- A Remotion composition that renders word-timed Arabic karaoke captions from a JSON word list.
- An After Effects MOGRT for a calm verse panel with a Quran font, its text supplied as data.
- An ffmpeg/ASS caption style with a dark scrim that stays legible over white clothing.
- A measured safe-zone table for one app, with the screenshots it came from.
- A test set of verse false-positives (isti'adha, basmala, formulas) and a detector that passes it.
- A checklist translated into Arabic.
- A recommendation from your own channel: what you decided, why, and what taught you.

## Code of conduct

- Be kind and patient. Assume good intent; correct with gentleness.
- Speak about ideas, not people. No mockery of anyone, inside or outside this project.
- Keep disagreements on matters of knowledge to evidence and to people qualified to judge them; where scholars
  differ, say so and do not force one view on the repository.
- No personal data of anyone in issues, pull requests or examples.
- Maintainers may edit, decline or remove contributions and comments that do not keep these.

## Licence of contributions

By contributing, you agree that your text is licensed under CC BY-SA 4.0 and any code under MIT, as described in the
[README](README.md#licence).
