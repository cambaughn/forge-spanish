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

## License

Copyright (c) Cameron Baughn.

Content is [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — use it, remix it,
build on it, just credit it.
