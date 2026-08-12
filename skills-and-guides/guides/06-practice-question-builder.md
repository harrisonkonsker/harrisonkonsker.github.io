# Practice Question Builder

> Turn a lecture's learning objectives into a practice exam that cannot skip anything.

**What it is:** A Claude workflow that writes practice questions from your lecture slides, with one hard rule: every learning objective gets covered, whether or not it looks interesting. It ends with an optional NBME-style section for anyone who wants harder, exam-style reasoning on top of the coverage.

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

### Step 6: Add the optional NBME-style section (run this last)

Everything above tests whether you learned the lecture. This section tests whether you can reason with it, in the style of a licensing exam: the diagnosis is never named, and the clues are present but not stated.

Run it only after the coverage table from Step 3 is clean. The ordering matters. These questions are deliberately not slide-bound, so if you generate them earlier they inflate the per-objective counts and an objective can pass the gate on the strength of a question that was never grounded in the first place.

> The objective-based questions are complete. Now add one final section titled "NBME-Style Questions (Optional Extra Practice)."
>
> Write 5 to 8 clinical vignette questions drawn from the objectives that involve a disease, presentation, diagnosis, or management decision. Do not try to cover every objective, and skip anything purely definitional. Under each question, note which objective it draws on.
>
> These questions are exempt from the slide-citation rule, but the concept being tested must still come from this lecture. You may add clinical detail the lecture did not provide in order to make the vignette realistic.

Then the style rules, which are the substance of the whole thing:

> Present every finding as raw data, never as an interpretation: "blood pressure 82/50 mm Hg" rather than "hypotensive," "temperature 38.9°C" rather than "febrile." Describe a rash instead of naming it. Never name the diagnosis, syndrome, organism, or drug class in the stem. Include two or three normal or incidental findings that do not point toward the answer. The answer must require combining at least two separate findings.
>
> Write exactly five options, all the same category, similar in length, in alphabetical order. Every distractor must be the correct answer to a slightly different vignette, and the rationale must name the finding a student would have to misread to choose it.
>
> Do not use "all of the above," "none of the above," negatively phrased stems, or absolute qualifiers.

The raw-data rule does most of the work. "Hypotensive and febrile" is the model doing your reasoning for you before you get a chance.

Have it open the section with this note, verbatim:

> These questions are harder than the ones above, on purpose. They may draw on material from other lectures or from later in the course, and they include clinical details this lecture never covered, added to make the vignettes realistic. They are optional extra practice, not a preview of your exam. The objective-based questions above are the ones matched to what this lecture actually taught. If a question here needs something you have not learned yet, treat that as information about what is coming rather than a mistake.

**Be clear with yourself about what this section is for.** It is practice for a licensing exam, not for your course exam. Many preclinical courses write their own questions that look nothing like NBME items. If your exam is written by your faculty, the objective-based questions above are the ones that matter, and this section is for later.

### Optional: harden a question you already have

Per-question work, so use it on the handful you care about rather than the whole batch. Open a **fresh** conversation and paste one question:

> Act as an item reviewer and find every reason a student could answer this correctly without clinical reasoning. Check for the diagnosis being named or hinted, an interpretation given where raw data belongs, a pathognomonic buzzword the real exam would omit, the correct answer being longer or more hedged than the distractors, a distractor that is obviously wrong to someone who never studied, and grammatical cueing between the lead-in and the correct option. Report the tells. Do not rewrite anything yet.

Then, in the same conversation:

> Now rewrite it with those tells removed, and state plainly what the student must now infer that they were previously told outright.

To go one level further, keep the vignette and move the question:

> Convert this into a second-order question. Keep the same vignette, but ask about the mechanism, the next step, or the expected complication, so that identifying the diagnosis becomes an unstated intermediate step rather than the answer itself.

First-order questions ask what the patient has. Real exam items often assume that and ask what follows.

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
