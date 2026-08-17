# Virtual Patient Simulator

> Practice taking a history from a patient who has the disease you just studied.

**What it is:** A ChatGPT workflow that turns a lecture into a patient you can interview. You ask the questions, the patient answers in their own words, and when you say "end encounter" the same model steps out of character and coaches you on what you missed.

**The problem it solves:** Six steps can teach you the facts about a disease. None of them teach you to sit across from the person who has it. Reading about a presentation is not the same as having to ask the right question to uncover it.

---

## Why this is different from a quiz

A practice question hands you the findings and asks for the diagnosis. A real patient hands you nothing. They tell you their ear hurts. Whether you ever learn about the rash, the facial weakness, or the hearing change depends entirely on what you think to ask.

That gap between recognizing information and eliciting it is where most of the actual skill of medicine lives, and it is the part that studying alone never touches.

---

## The workflow

This is one prompt, not four. Both roles are loaded at the start, and a keyword moves between them.

### Step 1: Set the scene

Attach the lecture, or just name the condition, and paste this:

> **Setup:** Specialty [cardiology · pulmonology · neuro · OB…], patient age, difficulty [beginner · intermediate · advanced], scope [history · +exam · +workup].
>
> **Role & Goal:** You're a realistic standardized patient during the encounter, and my coach afterward.
>
> **Ground Rules:** Stay in character and talk like a real patient, not a textbook. Never volunteer clues, reveal the diagnosis, or invent facts.
>
> **The Debrief:** When I say "end encounter," step out and coach me: what to keep, stop, and improve, the high-yield questions I missed, and a brief differential. Start when I say I'm ready.

Two rules carry most of the weight. **Never volunteer clues** is what leaves you something to practice; without it the model hands you the full case in its first reply. **Talk like a real patient, not a textbook** is what makes you translate: a patient says their face feels heavy, not that they have unilateral facial paresis.

The Setup line is what makes this reusable. Change four values and it is a different encounter, so one prompt covers every rotation rather than one disease.

### Step 2: Take the history

Interview them. Ask open questions first, then narrow. Push on anything vague.

You will feel the difference immediately: you have to *decide* what to ask. If you never ask about hearing, you never find out about the hearing change, and that omission is the lesson.

### Step 3: Say "end encounter"

Two words. The model drops the patient and becomes your coach: what to keep, what to stop, what to improve, the high-yield questions you missed, and a brief differential.

The trigger is the design, not a convenience. Because both roles are loaded from the start, the switch happens on your command rather than the model's judgment, so it never breaks character early to reassure you. And because you choose when to end it, you have already committed to your own read of the case before any coaching arrives. Say your diagnosis and your reasoning out loud before the keyword. Committing first is what makes the feedback land.

---

## Tips

- **Interview out loud if you can.** Use voice mode. Typing lets you compose a careful question; speaking forces you to ask it the way you would in a room.
- **Do not peek.** The temptation to ask "am I close?" mid-interview ruins it. Commit to an answer, then say "end encounter."
- **Turn up the difficulty rather than the disease.** The same condition at *advanced* is a different exercise from *beginner*, and it is closer to a real clinic than a new diagnosis is.
- **Ask for the hard version.** Request a patient who is a poor historian, is anxious, minimizes symptoms, or answers a different question than the one you asked.
- **Run the classic, then the atypical.** After a debrief, ask for the same condition with an atypical presentation and no warning about how it differs. The classic version is the one you would have recognized anyway.
- **One condition, several patients.** Running the same disease three different ways teaches the range of how it shows up, which is what recognition actually requires.

---

## What to watch out for

**Confirm before uploading.** Lecture slides may be proprietary to your school, and clinical material can contain protected health information. Check with the course director or professor before uploading a lecture, and never upload anything containing patient identifiers. Ask for a *generated* patient rather than pasting in a real case.

**The simulated patient is not a real patient.** The model will occasionally produce a presentation that does not quite hang together clinically. Treat disagreements as a prompt to check your slides, not as ground truth.

**This is practice for the skill, not a substitute for the encounter.** It builds the habit of asking systematically. It does not replace standardized patients, clinical skills coursework, or real patient contact.

**Built in ChatGPT, but the prompt is not tied to it.** Voice mode is the reason it was built there. The prompt itself is plain text and works in Claude or Gemini too, though you may need to restate the ground rules if a model starts coaching you mid-encounter.
