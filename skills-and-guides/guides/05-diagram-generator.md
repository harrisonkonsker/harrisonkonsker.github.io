# Lecture-to-Diagram (ChatGPT Workflow)

> **If the lecture doesn't click, draw it.** Upload the lecture to ChatGPT, get back a custom diagram organized by the most important categories of the content.

Not a custom skill: a workflow built around ChatGPT's image generation capability.

## What it does

Takes dense lecture content and generates a visual diagram that maps the concepts spatially. Useful when the lecture has too many moving parts to hold in your head, or when you're a visual learner and prose isn't sticking.

## What you need

- A ChatGPT account (Plus tier recommended for image generation reliability)
- A lecture PDF, slide image, or pasted text

## How to use

1. **Open** ChatGPT
2. **Upload** your lecture PDF or paste the relevant text
3. **Prompt:**

```
I'm studying for medical school and the attached lecture covers [TOPIC].
I need a diagram that helps me visualize this.

Please generate an image that:
1. Identifies the 3–5 most important categories in the lecture
2. Shows the relationships between them spatially (arrows, hierarchies, branches)
3. Uses color-coding so each category is distinct
4. Includes the key terms inside each category
5. Avoids being too dense: readability matters more than completeness

Output: a single clear diagram, not a wall of text. Use a clean medical textbook style.
```

4. **Refine**: if the first diagram isn't clear enough, say:
   - "Simplify this: show only the pathophysiology"
   - "Add the drug targets at each step"
   - "Use a flowchart layout instead of a hub-and-spoke"

5. **Save** the image to your study notes

## When to use it

- **Mechanism-heavy topics**: biochemistry cascades, immune responses, drug pathways
- **Differential diagnosis trees**: when distinguishing between similar conditions
- **Anatomy with relationships**: what connects to what, what drains where
- **Treatment algorithms**: first-line, second-line, contraindications

## Example use case

**Lecture topic:** The renin-angiotensin-aldosterone system (RAAS)

**Without diagram:** 8 paragraphs about juxtaglomerular cells, angiotensin I, angiotensin II, ACE, aldosterone, sodium retention, blood pressure changes...

**With diagram:** A single flowchart showing the cascade, color-coded by tissue (kidney, lung, adrenal), with each drug class (ACE inhibitors, ARBs, MR antagonists) labeled at its intervention point.

## Tips

- **Be specific about layout**: "flowchart," "hub-and-spoke," "Venn diagram," "decision tree" all produce different outputs
- **Don't try to fit everything**: diagrams fail when overloaded; ask for the 3–5 most important categories
- **Compare versions**: generate 2–3 variants and pick the one that clicks
- **Add to your Anki cards**: image cards are often easier to remember than text cards

## Why this works

The lecture doesn't change. *How your brain perceives it* changes. Diagrams force the spatial relationships into your visual cortex, which retains imagery far longer than prose.

---

Built by **Harrison B. Konsker** · Stanford MD Candidate · [harrisonkonsker.github.io](https://harrisonkonsker.github.io)
