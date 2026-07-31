# Anki Card Auto-Maker

> **The bottleneck has always been making the cards.** This skill removes it. Upload a lecture slide, get back finished Anki cards in perfect format.

## What it does

Takes a lecture slide (or full lecture PDF) and returns Anki-ready flashcards with:
- A clear question on the front
- A focused answer on the back
- Proper formatting for direct import or copy-paste
- One concept per card (no compound questions)

## Impact

- **Manual approach:** 12 hours per lecture to make 200 cards
- **With this skill:** ~10 minutes per lecture
- The time you used to spend *making* cards is the time you now spend *learning* from them

## What you need

- A Claude account
- An Anki account (free at [apps.ankiweb.net](https://apps.ankiweb.net))
- *Optional:* AnkiConnect for direct import

## How to use

### Step 1 — Generate cards from a slide

Paste this prompt into Claude with a lecture slide attached:

```
You are my medical school Anki card generator.

For the attached slide(s), generate Anki cards following these rules:

CARD STRUCTURE:
- One concept per card. No compound questions.
- Question on the front. Direct answer on the back.
- Use cloze deletions for lists, drug names, lab values
- Skip background context that isn't testable

WHAT TO INCLUDE:
- Mechanisms (cause and effect)
- Diagnostic criteria
- Treatment first-line / second-line / contraindications
- Lab values with normal ranges
- Anatomy with relationships
- Drug side effects, especially the unique or board-flagged ones

WHAT TO SKIP:
- Pure history (unless tested)
- Repetition of common knowledge
- Anything not from the lecture

OUTPUT FORMAT:
Q: [question]
A: [answer]
---

Output as many cards as the slide needs. No preamble.
```

### Step 2 — Import to Anki

**Quick path (copy-paste):**
1. Open Anki, create a new deck
2. Click "Add" → paste each Q/A pair manually

**Better path (bulk import):**
1. Save Claude's output as a `.txt` file
2. Use the format `Question[tab]Answer` (replace `Q: ` and `A: ` accordingly)
3. In Anki: File → Import → select your .txt file → choose "Fields separated by Tab"
4. All cards import at once

**Best path (AnkiConnect):**
1. Install [AnkiConnect add-on](https://ankiweb.net/shared/info/2055492159) in Anki
2. Tell Claude to format output as a JSON array and POST to AnkiConnect
3. Cards appear in Anki automatically

## Tips

- Run the skill on **one lecture at a time** — quality drops on giant batches
- Review the first 10 cards Claude generates before approving the rest — calibrate the model to your style
- Add the lecture title to each card as a tag (`#cardio-lecture-3`) so you can filter by topic later
- Combine with the **Lecture Distiller** for best results: distill → make cards from the distilled output

## Why this works with Anki specifically

Anki uses **spaced repetition** — the algorithm shows you cards at the moment your brain is about to forget them. Day 1, Day 3, Day 10, Day 25. Cards you find easy come back less often; cards you struggle with come back more often.

The bottleneck has always been making the cards. This skill removes it.

---

Built by **Harrison B. Konsker** · Stanford MD Candidate · [harrisonkonsker.github.io](https://harrisonkonsker.github.io)
