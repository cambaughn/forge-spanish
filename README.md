# Forge — Spanish course content

The complete content of [Forge](https://www.cambaughn.com/forge), a language-learning
app I built from 2018 to 2020. The company wound down during the pandemic, but the
Spanish course was finished. This is all of it, as data.

You can work through the course itself, for free and without an account, at
**[cambaughn.com/forge](https://www.cambaughn.com/forge)**.

## What's here

| file | |
|---|---|
| `sentences.json` | 1,534 Spanish/English pairs, with accepted alternates and distractors |
| `sentences.csv` | the same pairs, flat — for Anki, spreadsheets, anything that eats CSV |
| `lessons.json` | 301 lessons: 87 reading lessons and 214 drills |
| `course.json` | the main course — 18 units, 67 sections, 183 lessons, in order |
| `topics.json` | 19 themed collections across the same lessons (Star Wars, Cooking, Past Tense…) |
| `tips.json` | 20 short grammar notes, attached to individual sentences |
| `cheatsheets.json` | 19 longer reference pages, attached to units |

Every reference resolves. No ids point at anything missing.

183 of the lessons sit in the main course and 111 more are reached through a topic.
The remaining 7 are finished lessons that nothing links to — they were written and
then stranded, and they're here rather than thrown away.

## Shapes

A sentence. Only `id`, `es` and `en` are guaranteed; the rest appear when they have content.

```json
{
  "id": "es-a-donde-vas",
  "es": "¿A dónde vas?",
  "en": "Where are you going?",
  "en_alt": ["Where're you going?", "Where do you go?"],
  "tips": ["question-words", "ir"],
  "audio": "es-a-donde-vas.mp3"
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

## Audio

1,393 sentences have a recording, and `audio` holds its filename. 635 of those are
served today and can be fetched directly:

```
https://www.cambaughn.com/forge/audio/<filename>
```

The rest were recorded but aren't published yet. `audio` is absent where no recording
was ever made.

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
- **31 lessons**: 26 that were titles with no body, and 5 scratch records left over
  from testing (one of them three characters long).
- **Other languages.** There were small Esperanto, Italian and Chinese sets, plus
  single-record stubs. This repo is Spanish only.

## License

Content is [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — use it, remix it,
build on it, just credit it.
