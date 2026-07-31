# Virtual Patient Simulator

> Practice taking a history from a patient who has the disease you just studied.

**What it is:** A Claude workflow that turns a lecture into a patient you can interview. You ask the questions, the patient answers in their own words, and at the end you get feedback on what you missed.

**The problem it solves:** Six steps can teach you the facts about a disease. None of them teach you to sit across from the person who has it. Reading about a presentation is not the same as having to ask the right question to uncover it.

---

## Why this is different from a quiz

A practice question hands you the findings and asks for the diagnosis. A real patient hands you nothing. They tell you their ear hurts. Whether you ever learn about the rash, the facial weakness, or the hearing change depends entirely on what you think to ask.

That gap between recognizing information and eliciting it is where most of the actual skill of medicine lives, and it is the part that studying alone never touches.

---

## The workflow

### Step 1: Set up the patient

Attach the lecture (or name the condition) and paste this:

> You are going to role-play as a patient so I can practice taking a history.
>
> Pick one condition from this lecture and build a realistic patient who has it. Give them an age, an occupation, and a reason they came in today.
>
> Rules:
> - Stay in character as the patient. Answer only what I ask.
> - Do not tell me the diagnosis, and do not volunteer findings I have not asked about.
> - Describe symptoms the way a real person would, not in medical terms. If it burns, say it burns; do not say "dysesthesia."
> - If I ask a vague question, give a vague answer, the way a real patient would.
> - Do not coach me or hint that I am missing something.
>
> Start with one sentence about why you came in today, then wait for my questions.

The "do not volunteer" rule is what makes this useful. Without it, the model dumps the full case in the first reply and there is nothing left to practice.

### Step 2: Take the history

Interview them. Ask open questions first, then narrow. Push on anything vague.

You will feel the difference immediately: you have to *decide* what to ask. If you never ask about hearing, you never find out about the hearing change, and that omission is the lesson.

When you are ready to commit, state your diagnosis and your reasoning out loud before asking for feedback. Committing first is what makes the feedback land.

### Step 3: Ask for feedback

> Stop role-playing. I think this is [your diagnosis] because [your reasoning].
>
> Now give me feedback as an attending:
> - What was the actual diagnosis?
> - Which findings did I uncover, and which did I miss because I never asked?
> - What specific questions would have found the ones I missed?
> - What was the highest-yield question I never asked?

The most useful line in that list is the last one. There is usually a single question that would have cracked the case, and knowing which one it was transfers to the next patient.

### Step 4: Run it again with a twist

> Same condition, new patient. This time make the presentation atypical, and do not tell me how it differs.

The classic presentation is the one you will recognize anyway. The atypical version is the one that will fool you on the ward.

---

## Tips

- **Interview out loud if you can.** Use voice mode. Typing lets you compose a careful question; speaking forces you to ask it the way you would in a room.
- **Do not peek.** The temptation to ask "am I close?" mid-interview ruins it. Commit to an answer first, then get feedback.
- **Ask for the hard version.** Request a patient who is a poor historian, is anxious, minimizes symptoms, or answers a different question than the one you asked. That is closer to a real clinic than a cooperative patient.
- **One condition, several patients.** Running the same disease three different ways teaches the range of how it shows up, which is what recognition actually requires.

---

## What to watch out for

**Confirm before uploading.** Lecture slides may be proprietary to your school, and clinical material can contain protected health information. Check with the course director or professor before uploading a lecture, and never upload anything containing patient identifiers. Ask for a *generated* patient rather than pasting in a real case.

**The simulated patient is not a real patient.** The model will occasionally produce a presentation that does not quite hang together clinically. Treat disagreements as a prompt to check your slides, not as ground truth.

**This is practice for the skill, not a substitute for the encounter.** It builds the habit of asking systematically. It does not replace standardized patients, clinical skills coursework, or real patient contact.

**This works with any model.** Nothing here depends on a specific tool. The prompts work in Claude, ChatGPT, or Gemini.
