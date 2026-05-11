---
name: self-contained-topic-explainer
description: Create a self-contained, plain-language explainer for unfamiliar topics, concepts, domains, or source materials. Use when the user asks what something means, wants an accessible explanation of an unfamiliar field, asks to turn collected materials into an understandable article, or wants a reader to understand or apply a topic without needing to search elsewhere.
---

# Self-Contained Topic Explainer

Use this skill to explain unfamiliar topics in a way that is accessible, accurate, and complete enough that the reader does not need to search for basic missing context after reading.

## Trigger Examples

Use this skill when the user asks:

- "What is an LLM?"
- "Explain this concept in plain language."
- "I do not know this field; help me understand it."
- "Turn these notes into an easy-to-understand article."
- "Make this material understandable for beginners."
- "Write a complete explainer so the reader does not need to search elsewhere."

Do not use this skill for:

- Quick one-sentence definitions where the user explicitly wants brevity.
- Academic literature reviews whose main goal is citation coverage.
- News monitoring or current-state reporting without an explanatory article.
- Highly personalized professional advice where the user needs a domain expert.

## Workflow

1. Identify the target reader, their starting knowledge, and what they should understand or be able to do after reading.
2. Determine whether the topic is stable or time-sensitive.
3. If facts may have changed, or the topic involves law, medicine, finance, policy, product behavior, model capabilities, standards, or fast-moving technology, verify using reliable sources before writing.
4. If source material is provided, explain that material first instead of giving a generic overview.
5. Build a complete article outline where every major subtopic has its own section.
6. Write the explanation from intuition to precision: start with plain language, then introduce necessary terms.
7. Include practical examples, common mistakes, and ways to avoid them.
8. Add a Further Reading section with 3-5 high-quality sources and mark the best starting points.
9. Run the self-review checklist before finalizing.

## Required Article Structure

Use this structure unless the user requests a different format:

```markdown
# <Topic>

## TL;DR

<Short summary of the whole topic.>

## One-Sentence Definition

<A clear definition a beginner can remember.>

## Why This Matters

<Why the reader should care and where this appears in practice.>

## Core Idea

<The main intuition before technical detail.>

## Key Terms

<Define necessary terms in plain language.>

## <Major Subtopic 1>

<Dedicated explanation.>

## <Major Subtopic 2>

<Dedicated explanation.>

## Practical Examples

<Real or realistic examples, not just principles.>

## Common Mistakes And How To Avoid Them

<Mistakes, why they happen, and how to prevent them.>

## How To Apply Or Recognize This

<Checklist, procedure, decision guide, or diagnostic cues.>

## Further Reading

- [Best starting point] <source>: <why to read it>
- <source>: <why to read it>
- <source>: <why to read it>

## Self-Review

- Can the reader understand or apply this using only this article?
- Does every major subtopic have its own section?
- Are there practical examples, not only principles?
- Are common mistakes and avoidance strategies covered?
- Are all important facts in the main text rather than hidden in footnotes?
```

## Decision Rules

- Do not use footnotes. Put important context directly in the relevant section.
- Give each major subtopic its own section. Do not bury major ideas inside a catch-all paragraph.
- Prefer concrete examples over abstract claims.
- Explain jargon the first time it appears.
- Use analogies only when they clarify; do not let an analogy replace the accurate explanation.
- If the topic is complex, layer the explanation: simple intuition, precise model, practical implication.
- If there are multiple meanings of a term, separate them clearly.
- If sources disagree, explain the disagreement instead of flattening it.
- If the reader needs prerequisites, explain the minimum prerequisite inline.

## Source And Research Rules

- Prefer primary or authoritative sources: official documentation, standards, original papers, textbooks, reputable research organizations, or creator-maintained docs.
- For fast-moving topics, browse or otherwise verify current facts before presenting them as current.
- Use 3-5 sources in Further Reading, not a long bibliography.
- Mark 1-2 sources as "Best starting point" for beginners.
- Do not invent citations, links, paper titles, metrics, or claims.
- If no source was checked because the topic is stable and basic, say the explanation is based on general knowledge rather than fresh research.

## Style Rules

- Write for understanding, not for sounding expert.
- Prefer short sections, clear headings, and examples.
- Avoid unexplained acronyms.
- Avoid shallow lists that name concepts without explaining how they work.
- Include enough detail for the reader to act, recognize, or reason about the concept.
- When helpful, include a miniature example, comparison table, or step-by-step mental model.

## Self-Review

Before finishing, explicitly check:

- Can the reader understand or apply this using only this article?
- Is every major subtopic promoted into its own section?
- Are there real or realistic examples?
- Are common errors and avoidance strategies included?
- Is there a Further Reading section with 3-5 deep sources and marked starting points?
- Are time-sensitive claims verified or clearly scoped?
- Is anything important hidden in a footnote or vague aside? If yes, move it into the main text.
