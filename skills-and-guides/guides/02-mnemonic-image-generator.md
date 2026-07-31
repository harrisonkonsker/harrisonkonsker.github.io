# Mnemonic Image Generator

> **Because memory loves ridiculous.** A combined Claude + Gemini workflow that turns a hard-to-remember medical term into a single visual scene that encodes both the term's name and its meaning.

This is the tool I used to create the Gordon-Ramsay-in-a-Hunt-outfit image for Ramsay Hunt syndrome. I've made 140 of these in the past year for terms that refuse to stick.

## What it does

You give it a medical term. It returns:

1. A breakdown of the term into syllables that sound like familiar objects/people
2. A vivid AI image prompt that encodes both:
   - The **NAME** (via sound-alike visual hooks)
   - The **MEANING / function** (via scene composition)
3. A ready-to-use image you can save to Anki or your notes

## What you need

- **Claude** (Claude.ai or Claude Code): to generate the prompt
- **Gemini** (Google AI Studio, free): to generate the image
- *Optional:* an Anki account to save the image with your flashcard

## How to use

### Step 1: Generate the prompt in Claude

Paste this prompt into Claude:

```
You are a medical mnemonic image prompt generator.

Given a medical term, output a single vivid AI image prompt that encodes BOTH:
1. The NAME of the term (use sound-alike visual hooks broken into syllables)
2. The MEANING or function (encoded into the scene)

Output format:
TERM: [the term]
NAME BREAKDOWN: [syllable-by-syllable sound-alikes]
MEANING ENCODING: [what aspects of the meaning to show in the scene]
IMAGE PROMPT: [a single descriptive paragraph for an AI image generator]

The prompt should be specific, surprising, and slightly absurd. Memory works better when scenes are unusual.

Medical term: [PASTE TERM HERE]
```

Replace `[PASTE TERM HERE]` with your term. Claude returns the full breakdown plus an image prompt.

### Step 2: Generate the image in Gemini

1. Go to [Google AI Studio](https://aistudio.google.com)
2. Switch to the **Imagen** model (or use Gemini's image generation)
3. Paste the IMAGE PROMPT from Claude's output
4. Generate: usually takes ~10 seconds
5. Download the image you like best

### Step 3: Save it

- **Anki:** attach the image to your flashcard's back side
- **Notion / Obsidian:** drop it into your notes
- **Phone:** add to a "med-mnemonics" album for quick review

## Why two AI tools?

- **Claude** is better at the linguistic puzzle (breaking syllables, encoding meaning)
- **Gemini's Imagen** produces sharper, more detailed images than Claude's image generation

Use Claude for the thinking, Gemini for the drawing.

## Example (Ramsay Hunt Syndrome)

**Term:** Ramsay Hunt syndrome type II

**Output:** Gordon Ramsay in a brown hunting outfit, holding cranial nerve VII like a fishing rod, standing in a forest filled with chickenpox-virus pumpkins. His ear has painful red vesicles. A clock in the background reads "72 hours."

This single scene encodes:
- Ramsay (Gordon Ramsay)
- Hunt (hunting outfit)
- Cranial nerve VII (fishing rod with VII)
- VZV / chickenpox (pumpkins)
- Painful ear vesicles (red ear)
- 72-hour treatment window (clock)

## Tips

- **Be specific**: vague image prompts produce vague images. Describe textures, colors, lighting.
- **Embrace absurdity**: your brain remembers absurd before plausible
- **One scene per term**: don't try to encode multiple terms in one image
- **Save the prompt + image together**: when you want to remember why the image works, you'll need the syllable breakdown

---

Built by **Harrison B. Konsker** · Stanford MD Candidate · [harrisonkonsker.github.io](https://harrisonkonsker.github.io)
