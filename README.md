# Forge — Spanish course content

The complete content of [Forge](https://www.cambaughn.com/forge), a language-learning
app I built from 2018 to 2020. The company wound down during the pandemic, but the
Spanish course was finished. This is all of it, as data.

You can work through the course itself, for free and without an account, at
**[cambaughn.com/forge](https://www.cambaughn.com/forge)**.

## What's here

| file | |
|---|---|
| `sentences.json` | 1,512 Spanish/English pairs, with accepted alternates and distractors |
| `sentences.csv` | the same pairs, flat — `id,spanish,english`, for Anki or a spreadsheet |
| `lessons.json` | 294 lessons: 86 reading lessons and 208 drills |
| `course.json` | the main course — 18 units, 67 sections, 183 lessons, in order |
| `topics.json` | 19 themed collections across the same lessons (Star Wars, Cooking, Past Tense…) |
| `tips.json` | 20 short grammar notes, attached to individual sentences |
| `cheatsheets.json` | 19 longer reference pages, attached to units |

Every reference resolves, and every lesson is reachable: 183 sit in the main course,
and the other 111 are reached through a topic.

## Shapes

A sentence. Only `id`, `es` and `en` are guaranteed; the rest appear when they have content.

```json
{
  "id": "es-a-donde-vas",
  "es": "¿A dónde vas?",
  "en": "Where are you going?",
  "en_alt": ["Where're you going?", "Where do you go?"],
  "tips": ["question-words", "ir"]
}
```

A lesson is either prose or a drill:

```json
{ "id": "es-sounds-of-spanish", "type": "reading", "title": "Sounds of Spanish", "text": "..." }
{ "id": "es-yes-and-no", "type": "drill", "title": "Yes and no", "sentences": ["es-si", "es-no", "..."] }
```

`course.json` nests units → sections → lesson ids. `topics.json` is a flat list of
lesson ids per topic. Both point into `lessons.json`; drills point into `sentences.json`.

Lesson and cheat-sheet text is Markdown.

## What was left out, and why

The original data had several half-finished migrations in it. Rather than ship the
confusion, I cut:

- **The word-level hints.** Every sentence mapped word positions to dictionary entry
  ids. That dictionary was never exported and no longer exists, so the hints couldn't
  be resolved by anyone.
- **Vocab packs.** 21 word lists whose 611 entries point at the same missing dictionary.
  609 of 611 are unresolvable.
- **`packs`.** The original container. 30 became topics, 14 became units; the rest were
  stranded.
- **A separate `questions` collection.** Superseded by `sentences` — of 1,474 drill
  references, exactly one still needed it, and that one was a test record.
- **`cheat_sheet_entries`.** A newer take on cheat sheets that nothing referenced, and
  which duplicated an existing tip word for word.
- **38 lessons**: 26 that were titles with no body, 5 scratch records left over from
  testing (one of them three characters long), and 7 that nothing linked to — five
  of those belonged to topics that were never finished.
- **22 duplicate sentence records.** The same Spanish sentence was sometimes entered
  twice, once per lesson that needed it, and the copies drifted apart: one version of
  *¿Dónde estás?* accepted "Where are you at?" and the other didn't, so the same prompt
  was graded two different ways. They're merged, with the accepted answers combined.
- **The audio.** Most of these sentences were recorded, but the recordings aren't
  part of this release. This is the text.
- **Other languages.** There were small Esperanto, Italian and Chinese sets, plus
  single-record stubs. This repo is Spanish only.

## License

Content is [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — use it, remix it,
build on it, just credit it.
