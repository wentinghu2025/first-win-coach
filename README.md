# First Win Coach

**One better request changes what AI gives you back.**

**▶ Live demo: [wentinghu2025.github.io/first-win-coach](https://wentinghu2025.github.io/first-win-coach/)**

First Win Coach is an interactive prototype that teaches people in non-tech jobs how to get useful work out of AI. Instead of a course, it walks through two realistic workplace stories. In each one, a worker's first request to AI goes wrong, the user fixes it by adding facts the worker already has, and then the user writes a request for a new situation on their own.

## Try it

- **Online:** open **[https://wentinghu2025.github.io/first-win-coach/](https://wentinghu2025.github.io/first-win-coach/)**. No account or install needed; works on phones too.
- **Offline:** download [`index.html`](index.html) and double-click it. It's a single self-contained file.

Each story takes about 4 minutes. Every answer is pre-scripted, so the demo behaves the same way every time and needs no account or API key.

## The two stories

| Story | Situation | What goes wrong on the first try |
| --- | --- | --- |
| **Tom**, store manager | Must answer a public 1-star review before the store opens at 9 | The AI invents fixes that never happened, offers 20% off (over Tom's $10 limit), and signs as "The Management Team" |
| **Maria**, office administrator | Must turn scribbled meeting notes into minutes for her director by noon | The AI states undecided items as decisions, invents a date, drops owners and deadlines, and adds filler |

## How each story works

| # | Chapter | What happens |
| --- | --- | --- |
| 01 | The situation | Real documents: the review or notes, plus texts, schedules, policies and emails the worker has but hasn't given the AI |
| 02 | First try | A one-line request and the AI's answer, with every problem highlighted and explained |
| 03 | Try again | Tick the facts the worker already knows; each one adds a line to the request and rewrites the answer live |
| 04 | Check before sending | Every fact in the answer is traced to its source, or flagged |
| 05 | Sent | The answer in the real world, and how the customer or boss replies |
| 06 | Your turn | A new situation. Write the request yourself, with no checklist, and see the result |

## Updating the demo

The live demo is published from the `main` branch with GitHub Pages. To change it, edit `index.html` (on GitHub: open the file, click the pencil icon, then **Commit changes**). The live site updates within a minute or two; refresh with Ctrl+F5 (Windows) or Cmd+Shift+R (Mac) if you still see the old version.

## Repository structure

```
.
├── index.html   # The interactive demo (self-contained: HTML, CSS, JS, photos)
├── PRD.md       # Product requirements for this prototype
└── README.md    # This file
```

## Editing the stories

All content lives in `index.html`, in the `TOM` and `MARIA` objects at the top of the `<script>` block. No build step is needed: edit, save, refresh.

| Field | What it controls |
| --- | --- |
| `primary`, `knows` | The documents shown in chapter 1 |
| `options` | The five facts in chapter 3: title, source, and the line each adds to the request |
| `compose` | The answer engine for the main story (one sentence variant with and without each fact) |
| `claims` | The source checks in chapter 4 |
| `posted` | The reader's reply in chapter 5, based on how many problems remain |
| `turnPrimary`, `turnKnows`, `turnCompose` | The "Your turn" situation and its answer engine |
| `detect`, `hints` | Keyword patterns that recognize each fact in the user's own request, and example sentences for missed facts |

Each problem in an answer is defined by the exact phrase to highlight and a one-line explanation. If you change an answer's wording, keep the highlighted phrases in sync.

To swap a photo, replace the `photo:` value in `TOM` or `MARIA` with a relative path or a data URI.

## Status and next steps

Round 1 prototype, ready for pilot testing with 3–5 target users, followed by 8–10 moderated sessions and a delayed transfer check. See [PRD.md](PRD.md) for the research plan, metrics and open questions.

## Notes

- Fonts load from Google Fonts when online; the page falls back to system fonts offline.
- The page supports light and dark mode, works at phone width, and respects reduced-motion settings.
- People, businesses and documents in the stories are fictional.
