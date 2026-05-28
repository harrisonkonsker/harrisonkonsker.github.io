# Lecture Distiller

> **One slide is one problem. A lecture is 120 of them.** This skill turns 120 disorganized slides into 4 cleanly organized sections in ~5 minutes.

A custom Claude skill that takes a dense medical lecture (PDF) and splits it into four study-ready categories:

1. **Pathophysiology**
2. **Clinical presentation**
3. **Differential diagnosis**
4. **Clinical correlations**

## Impact

- **Before:** ~3 hours of manual organizing per lecture
- **After:** ~5 minutes
- The hours saved go directly to learning, not formatting

## What you need

- A Claude account (Claude.ai or Claude Code)
- A lecture in PDF format

## How to use

### Option A — Claude Code (most powerful)

1. Save the skill files to `~/.claude/skills/lecture-distiller/SKILL.md`
2. Restart Claude Code
3. Drop your lecture PDF into the conversation and say:
   > "Use the lecture-distiller skill on this lecture."
4. Claude returns a formatted study guide with all four sections.

### Option B — Claude.ai

1. Open a new Claude conversation
2. Attach your lecture PDF
3. Paste this starter prompt:

```
You are my preclinical medical education study assistant.

Take the attached lecture and organize it into a structured study guide with exactly these four sections:
1. Pathophysiology — mechanisms, biological cascades, key cell types
2. Clinical Presentation — signs, symptoms, classic patient story
3. Differential Diagnosis — what else could it look like, how to distinguish
4. Clinical Correlations — exam findings, lab values, imaging, board pearls

CRITICAL RULES:
- Only use facts from the lecture. Do not add information from external sources.
- Preserve exact terminology used by the lecturer.
- Use bullet points and short phrases, not long sentences.
- Flag anything the lecturer emphasized as "high-yield" or "memorize this."

Output the four sections in order. No preamble.
```

4. Send and wait. Claude will return the organized guide.

## Tips

- Works best on lectures 50–200 slides long
- For .pptx files: export to PDF first
- The skill is anti-hallucination by design — it only uses what's in your lecture, not board prep textbooks
- Save the output as a Google Doc or Notion page for later review

## Why it works

Medical lectures are organized for the lecturer, not the learner. The same fact often appears across three different slides. The distiller groups every fact by its **role in the clinical picture**, so when you study, you study the disease, not the slide order.

---

Built by **Harrison B. Konsker** · Stanford MD Candidate · [harrisonkonsker.github.io](https://harrisonkonsker.github.io)
