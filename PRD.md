# PRD: First Win Coach (Round 1 Prototype)

| | |
| --- | --- |
| **Status** | Round 1 prototype, ready for pilot testing |
| **Last updated** | October 17, 2026 |
| **Demo** | [`index.html`](index.html) (open in any browser, or via GitHub Pages) |
| **Audience for this doc** | Product, design, research and engineering on the team |

---

## 1. Summary

First Win Coach is an interactive prototype that teaches people in non-tech jobs how to get useful work out of AI. It does this through two realistic workplace stories rather than a course.

In each story, a worker's first request to AI goes wrong in specific, visible ways. The user then fixes the request by adding facts the worker already has: a text from a colleague, a schedule, a policy, an email from the boss. Every fact the user adds visibly changes the AI's answer. Finally, the user writes a request for a new situation on their own.

The core idea fits in one line:

> **One better request changes what AI gives you back.**

## 2. Problem

People in non-tech roles (store managers, office administrators, teachers, HR coordinators) try AI once or twice and give up. When we look closely, the pattern is consistent:

- **They ask in one line.** "Write a reply to this review." "Summarize these notes."
- **The AI fills the gaps.** With no context, it produces generic filler, invents facts and commitments, and guesses at things that were never decided.
- **They blame the tool.** The answer "sounds like a robot", so they conclude AI isn't useful for their job.

The missing skill is not prompt engineering. It is **knowing which facts you already have that the AI needs**, and **checking the answer against them** before using it.

Existing options don't teach this well:

- **AI tools** do the work for the user. The user gets an answer, not a skill.
- **Courses and prompt libraries** teach abstract frameworks that users don't connect to their own Monday morning.

## 3. Target users

Primary users are adults in non-technical roles who have used AI rarely or never, and who want help with everyday work.

| Persona | Role | Situation in the prototype | What they believe about AI today |
| --- | --- | --- | --- |
| **Tom** | Store manager, Hillside Market | Must answer a public 1-star review before the store opens | "I tried it twice. It sounded like a robot." |
| **Maria** | Office administrator, Brightwater Property Group | Must turn scribbled meeting notes into minutes for her director by noon | Uses it occasionally; doesn't trust it with anything that goes to her boss |

## 4. Hypothesis and positioning

**Hypothesis.** Users learn to use AI more independently when they see, side by side, how the same AI responds to a thin request and to a request that carries their real context, and then practice writing one themselves.

**The test for every design decision.** Does this help people become better at using AI, rather than simply doing better work for them?

**Positioning.** We teach transferable AI literacy, not Claude features. The skills (give context, state limits, don't let it guess, check before sending) work in any AI tool. Claude is the learning partner.

## 5. Prototype scope

### In scope (Round 1)

| Story | Task type | Why this story |
| --- | --- | --- |
| **Tom: reply to a customer review** | Draft something new | Shows invented promises, tone problems and policy limits. Easy to see real-world consequences. |
| **Maria: meeting notes to minutes** | Structure messy information | Shows guessing (undecided items stated as decisions), invented dates, missing owners and wrong format. |

Each story includes one **same-type transfer task**: a new review for Tom (a birthday cake order gone wrong), a new email thread for Maria (a lobby repaint), which the user handles on their own.

### Out of scope (Round 1)

- Live AI calls. Every answer is pre-scripted (see section 8).
- Additional roles and scenarios (teacher, HR, nurse, small business, sales). These stay in the long-term scenario library.
- Healthcare scenarios, which need stricter privacy and safety design first.
- Accounts, progress tracking across sessions, skill maps.
- Cross-type transfer (for example, Structure to Draft). We test same-type transfer first.

## 6. Experience design

The home screen states the promise in one sentence and offers two people to help. Each story is a single scrolling page of six chapters. Each chapter is revealed by a "Continue" button, and earlier chapters stay visible so the user can look back.

| # | Chapter | What the user sees and does | What it teaches |
| --- | --- | --- | --- |
| 01 | **The situation** | A clock ("Monday 8:40 a.m., store opens at 9"), the primary document (the review, or the handwritten notes), and 3–4 real artifacts the worker has: texts, a schedule, a policy, the boss's email. Labeled "What Tom knows, but hasn't told the AI." | The context already exists. It's just not in the request. |
| 02 | **First try** | The worker's one-line request and the AI's answer. Every problem is highlighted and numbered, with a plain explanation underneath. | Thin requests produce filler, invented facts and guesses. The AI isn't careless; it only knew what it was told. |
| 03 | **Try again, with what they know** | Five facts as checkboxes, each labeled with its source ("From: Rosa's text"). Ticking a fact adds a sentence to the request (left) and rewrites the answer (right). A counter shows problems left, word count and facts added. | Each fact fixes a specific problem. The user sees cause and effect directly. |
| 04 | **Check it before sending** | Each fact in the final answer, with where it came from, or a warning if nothing backs it. The user can go back and fix, or send anyway. | Verify against real sources before using AI output. |
| 05 | **Sent / posted** | The answer as it appears in the real world (a review site, an email), plus the reader's reply. A good answer earns "I'll give you another try"; a bad one gets "I asked for a manager and got a form letter." | Mistakes have consequences for real people. |
| 06 | **Your turn** | A new situation of the same type. The user writes the request in an empty box, with no checklist. The prototype shows the AI's answer, which facts the request covered (with an example sentence for each one missed), what went wrong because of what was missing, and a five-line takeaway. | Independent transfer: can the user do it without scaffolding? |

### Mapping to the learning loop

| Learning loop step | Where it happens |
| --- | --- |
| Show me | Chapter 2: a worked example of what goes wrong, and why |
| Let me try | Chapter 3: the user chooses which facts to add |
| Coach me | Chapters 3–4: instant, specific feedback on each choice |
| Transfer it | Chapter 6: a new task, written from scratch |

## 7. Story specifications

### 7.1 Tom: reply to a customer review

**Primary document.** Jordan P., 1 star: waited 25 minutes at checkout with 2 lanes open; rotisserie chicken cold in the middle; asked for a manager and nobody came.

**What Tom knows.**

- Text from Rosa (deli lead), Sunday 7:12 a.m.: the hot-case thermometer read 20° low on Saturday; replaced Sunday morning.
- Saturday schedule: 2 of 4 cashiers called in sick.
- Store policy 4.3: managers may offer a credit of up to $10 without district approval.
- Tom was in the back checking in a delivery; nobody came to get him.

**First request:** "Write a reply to this review."

**The five facts, and what each one fixes:**

| Fact | Line added to the request | Source | Problem when missing |
| --- | --- | --- | --- |
| Who's speaking, public | "I'm Tom, the manager of Hillside Market. This reply will be posted publicly…" | Tom's role | "Dear Valued Customer", signed "The Management Team" |
| What happened | "2 of our 4 cashiers called in sick… nobody came to get me." | Saturday schedule | Vague sympathy; ignores the missing manager |
| The real fix | "The hot-case thermometer was reading low. We replaced it on Sunday. Only mention fixes we've actually made." | Rosa's text | Invents "retrained our entire deli team" and "four lanes open every weekend" |
| What you can offer | "I can offer up to a $10 credit. Don't promise anything else." | Policy 4.3 | Offers 20% off, over Tom's limit |
| Length and tone | "Under 90 words. Apologize once. Sound like a person." | Tom | Filler ("Your satisfaction is our top priority") |

**Transfer task.** Marcus D., 2 stars: birthday cake ready 40 minutes late, name spelled wrong. Context: Oven 2 was down Friday 1–3 p.m.; the bakery now reads names back on phone orders; order slip shows the misspelling; same $10 policy.

**Takeaway shown to the user.** Next time you ask AI to answer a customer, tell it: who is speaking and that it will be public; what actually happened; the real fix, only what you've already done; what you're allowed to offer; how long, and to sound like a person.

### 7.2 Maria: meeting notes to minutes

**Primary document.** Handwritten notes from the 10/14 ops sync: printer broken, "tech coming thurs?"; party budget $1,200, Priya to book venue by 10/31, "Tom wants potluck instead??"; iPad sign-in starts Nov 3; parking permits expire "end of month"; Q4 supply requests due 10/21, order due 10/24.

**What Maria knows.**

- Email from Sam (director), 11:05 a.m.: minutes by noon, keep it short, only decisions and who's doing what.
- Last month's minutes: the format Sam likes (Decisions / Action items with owner and due date / Still open).
- Her memory: nobody agreed to the potluck; Raj wasn't sure the technician is coming Thursday.

**First request:** "Summarize these meeting notes."

**The five facts, and what each one fixes:**

| Fact | Line added to the request | Source | Problem when missing |
| --- | --- | --- | --- |
| Who reads it | "These minutes go to Sam… He only wants what we decided and who's doing what." | Sam's email | Generic "Meeting Summary" title |
| The format | "Use three parts: Decisions, Action items (owner and due date), Still open." | Last month's minutes | One paragraph; owners and dates lost ("due soon") |
| Don't guess | "If something wasn't decided or has a question mark… put it under Still open." | Maria's memory | States "decided on a potluck" and "technician coming Thursday" as fact |
| Dates as written | "Don't turn 'end of month' into a date." | Her notes | Invents "October 31" |
| Length | "Under 120 words. No filler." | Sam's email | "A productive meeting with good progress" |

**Transfer task.** A six-message email thread about repainting the lobby, to be summarized for the whole office on Slack. Context: Kim (Ana's manager) hasn't approved Ana's request for Monday morning off; 40 people read the channel, most only the first two lines.

**Takeaway shown to the user.** Next time you ask AI to summarize a meeting or a thread, tell it: who reads it and what they need; the format they expect; not to guess, so undecided things stay open; to keep dates and numbers exactly as written; how long it should be.

## 8. System behavior

### Why the prototype is fully scripted

A demo and a research prototype must behave identically every time. Live AI calls add latency, cost, variability and consent prompts, and they make it impossible to guarantee that "missing fact X causes problem Y" is visible on screen. Round 1 tests the learning mechanism, not model quality.

### How answers are generated

Each story defines five boolean facts. The answer is assembled from sentence variants: one "with the fact" version and one "without the fact" version for each part of the answer. This gives 32 coherent answers per story, and each problem is tied to the absence of exactly one fact.

- Problems are stored with the exact phrase to highlight and a one-line explanation.
- An automated check confirms that every highlighted phrase appears in its answer for all 32 combinations of both stories and both transfer tasks.

### "Your turn" detection

The user's free-text request is matched against simple keyword patterns per fact (for example, `$10`, `credit` or `limit` counts as "set what you can offer"). The detected facts drive the same answer engine, so the user sees the consequence of what they wrote. Known limitation: keyword matching can be fooled. It is adequate for moderated sessions, not for production.

### Technical notes

- Single self-contained HTML file: no build step, no backend, no external calls except Google Fonts (with system-font fallbacks, so it works offline).
- Photos are embedded as data URIs.
- Works at phone width; respects light and dark mode and reduced-motion settings.

## 9. Design principles

1. **Real material carries the page.** Reviews, texts, schedules and handwritten notes, not diagrams and frameworks.
2. **Show cause and effect.** Every fact the user adds changes something visible.
3. **Consequences, not lectures.** The customer's or boss's reply teaches more than a tip box.
4. **Name skills last, in plain words.** The five-line takeaway appears only after the user has done the work.
5. **The user does the final step alone.** No checklist in "Your turn."

## 10. Success metrics and research plan

### Round 1 research questions

1. Can users complete a useful work task without being slowed down by teaching?
2. Does seeing the before/after improve the quality of the user's own request?
3. Can users transfer the same skill to a new situation of the same type?
4. Can users identify information that needs checking before sending?
5. Does the experience feel helpful rather than like a class?

### Measures

| Outcome | Measure | How |
| --- | --- | --- |
| Request quality | Facts covered in the "Your turn" request (0–5) | Logged by the prototype; reviewed by moderator |
| Baseline vs. after | Facts covered in a request written before the story vs. in "Your turn" | Pre-task in session (see below) |
| Safe judgment | Whether the user notices invented or unverified claims in chapter 4, and chooses to fix or send | Observation |
| Understanding | Can the user explain, in their own words, why the first answer went wrong? | Debrief question |
| Experience | Perceived usefulness and intrusiveness (1–5) | Post-session survey |
| Delayed transfer | Facts covered in a fresh request 7–14 days later, without the prototype | Follow-up task |

### Session plan (8–10 moderated sessions; pilot with 3–5 first)

1. **Baseline (5 min).** Participant writes an AI request for a familiar work task, with no help.
2. **Story (10 min).** Participant goes through one story; moderator observes chapter 3 choices and chapter 4 decision.
3. **Transfer (5 min).** "Your turn" in the same story.
4. **Debrief (5 min).** Explain what changed; when would you check an AI answer?
5. **Follow-up (7–14 days later).** A new task of the same type, without the prototype.

## 11. Risks and open questions

| Risk | Mitigation |
| --- | --- |
| Users treat the checkboxes as a quiz and tick everything without reading | Problems counter and highlights make each tick's effect visible; moderator asks why |
| Scripted answers feel fake to sharp users | Answers are realistic and specific; a later round adds a live mode |
| Keyword detection in "Your turn" misjudges a request | Moderated sessions only; show examples for missed facts rather than a score |
| Two stories don't represent all roles | Round 1 tests the mechanism; library expands after validation |

**Open questions**

- Should the first try be the user's own one-line request instead of the scripted one?
- B2C, or deployed by employers? This affects privacy design and which stories we build next.
- Which languages and regions should the pilot cover?

## 12. Next steps

1. Pilot with 3–5 target users; fix flow problems.
2. Run 8–10 moderated sessions and the delayed transfer check.
3. Add a third story only if same-type transfer works.
4. Explore a live mode where "Your turn" calls Claude and coaches the user's actual wording.

## Appendix: editing the stories

All story content lives in `index.html`, inside the `TOM` and `MARIA` objects near the top of the script:

- `options`: the five facts (title, source label, line added to the request).
- `compose` / `turnCompose`: the answer engine for the main story and the transfer task.
- `claims`: the chapter 4 source checks.
- `posted`: the reader's reply, based on how many problems remain.
- `detect` and `hints`: keyword patterns and example sentences for "Your turn".
