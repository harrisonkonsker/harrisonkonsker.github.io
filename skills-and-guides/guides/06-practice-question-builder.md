# Practice Question Builder

> Turn a lecture's learning objectives into a practice exam that cannot skip anything.

**What it is:** A Claude workflow that writes practice questions from your lecture slides, with one hard rule: every learning objective gets covered, whether or not it looks interesting.

**The problem it solves:** When you ask an AI for practice questions, it gravitates toward the memorable clinical material and quietly skips the plain mechanism and definition objectives. Those are exactly the ones that show up on exams. This workflow makes skipping structurally impossible.

---

## Why the structure matters

Most people ask "write me practice questions about this lecture" and take what they get. The output looks good, so you trust it. The gap only becomes visible on exam day, when you get tested on an objective the AI never drilled.

The fix is not a better prompt. It is a **validation gate**: generate the questions, then check them against the objectives and refuse the batch if any objective is missing. Regeneration is cheap. Discovering the gap on the exam is not.

---

## The workflow

### Step 1: Extract the learning objectives verbatim

Attach the lecture (PDF or slides) and ask:

> Extract every learning objective from this lecture, word for word. Number them. Do not summarize, merge, or reword them. If an objective has numbered sub-parts, keep each sub-part.

Verbatim matters. Paraphrasing collapses distinct objectives together, and merged objectives are how coverage gaps start.

### Step 2: Generate questions with a per-objective quota

> For each learning objective, write 4 to 6 practice questions: at least 3 multiple choice and at least 1 free response.
>
> Scale the count to the content: 4 questions for a single concept on 1 to 2 slides, 5 for a multi-part objective on 3 to 5 slides, 6 for a multi-step or matrix topic on 6 or more slides.
>
> Rules:
> - Every question must be answerable from the slides. Cite the slide number for each one.
> - Each objective needs at least one recall/understand question AND one apply/analyze question.
> - You may not skip an objective for being "too basic" or "just a definition."
> - Every multiple-choice question needs a one-line rationale for each option, explaining why the wrong ones are wrong.

The quota is what forces coverage. Without a per-objective number, the model spends its effort on the interesting third of the lecture.

### Step 3: Run the coverage gate (the step people skip)

Start a **fresh** conversation, attach the objectives and the questions, and ask:

> Here are the learning objectives and the practice questions. For each objective, list how many questions cover it. Flag any objective with fewer than 4 questions or zero free-response questions. Do not fix anything. Just report the table.

Use a new conversation so the model audits the work instead of defending it. Then send the gaps back for regeneration and re-audit until the table is clean.

### Step 4: Check the questions are actually grounded

> For each question, quote the exact line or figure from the slides that supports the correct answer. If you cannot find slide support, mark the question UNGROUNDED.

Anything ungrounded is either invented or pulled from outside knowledge. Delete it or rewrite it from the slide. This is the single highest-value check in the workflow, because a plausible wrong question teaches you a plausible wrong fact.

### Step 5: Fix the quality tells

Ask for these specifically, because they show up constantly:

> Check for: answers clustering on one letter (spread them); the correct answer being noticeably longer than the distractors (equalize the lengths); parenthetical hints that give away the answer (remove them); two options that mean the same thing.

Length bias and letter bias are the two habits that make AI-written questions trivially easy in a way that flatters you during review and fails you on the exam.

---

## Tips

- **Keep the objectives and the questions in separate files.** It makes the audit step much easier to run honestly.
- **Log what you miss.** Keep a running list of concepts you get wrong, and feed it in when generating the next batch so your weak areas get extra questions.
- **Free-response questions are worth the effort.** Multiple choice lets you recognize the answer; free response makes you produce it, which is closer to what an exam or a patient asks of you.
- **Do the audit in a new chat every time.** A model that just wrote 25 questions is a poor judge of whether it covered everything.

---

## What to watch out for

**Confirm before uploading.** Lecture slides may be proprietary to your school or faculty, and some clinical material contains protected health information. Check with the course director or professor before putting a lecture into an AI tool, and never upload anything with patient identifiers.

**AI-written questions are practice, not truth.** A question can be well-formed and still medically wrong. If a rationale surprises you, verify it against your slides or a reference before you commit it to memory.

**This works with any model.** The workflow is the substance, not the specific tool. The prompts above work in Claude, ChatGPT, or Gemini.
