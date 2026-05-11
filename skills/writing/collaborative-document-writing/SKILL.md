---
name: collaborative-document-writing
description: Collaboratively plan, draft, revise, and validate documents with the user while preserving their intent and voice. Use when the user asks to coauthor, write together, draft a document, improve a document through discussion, create a PRD/design doc/proposal/report/guide, or iteratively shape writing instead of receiving a one-shot answer.
---

# Collaborative Document Writing

Use this skill to act as a document coauthor. Build the document with the user through context gathering, outline agreement, focused drafting, revision, and reader-centered validation.

## Trigger Examples

Use this skill when the user asks to:

- "Help me write this document with me."
- "Let's draft a PRD together."
- "Coauthor this design doc."
- "Ask me questions first, then write the proposal."
- "Help me turn these notes into a polished doc."
- "Iterate on this document section by section."

Do not use this skill for:

- Short copy edits where the user only wants grammar or tone fixes.
- Pure summarization with no coauthoring or revision loop.
- Code implementation plans unless the user wants a human-readable document as the deliverable.

## Workflow

1. Identify the document type, audience, purpose, desired outcome, tone, and delivery format.
2. Inspect any source material the user provides: notes, existing docs, code, data, tickets, transcripts, or links.
3. Ask only the most important missing question when context is insufficient. Prefer moving forward with clearly labeled assumptions.
4. Propose a compact outline before drafting when the document is more than a short section.
5. Draft in reviewable chunks. For long documents, work section by section instead of producing a giant first pass.
6. Preserve the user's intent, terminology, and voice. Improve clarity without replacing their perspective.
7. Mark uncertain content with `[Assumption]`, `[TODO]`, or `[Needs confirmation]`.
8. After revisions, run a new-reader check and suggest the smallest useful final polish pass.
9. Run final review before calling the document complete.

## Collaboration Modes

- Discovery: Ask targeted questions to clarify goal, audience, constraints, and source material.
- Outline: Create or revise the document structure before drafting.
- Drafting: Write a first pass that is easy to edit, with assumptions clearly marked.
- Revision: Apply user feedback while preserving already-approved decisions.
- Polishing: Improve flow, specificity, headings, transitions, and actionability.
- Reader test: Read as the intended audience and identify confusion, missing context, or weak claims.
- Final review: Confirm the document is ready for ownership, publication, or handoff.

## Decision Rules

- If the user asks for collaboration, do not dump a full long document before aligning on purpose and outline.
- If the user asks for a quick first draft, produce a usable draft and list the assumptions instead of blocking on questions.
- If the document has high stakes, separate facts, assumptions, recommendations, and open questions.
- If source material conflicts, call out the conflict and ask which source should win.
- If the document is for a specific audience, optimize examples, vocabulary, and level of detail for that audience.
- If the user's wording carries important nuance, preserve it unless clarity requires a change.
- If external facts, laws, prices, current product behavior, or recent events matter, verify them before presenting them as true.

## Document Quality Checklist

Before treating a draft as ready, check:

- Purpose: The reader can tell why the document exists.
- Audience: The level of detail fits the intended reader.
- Structure: Headings create a clear path through the argument.
- Claims: Important claims are supported or marked as assumptions.
- Actionability: Decisions, asks, next steps, or owners are explicit when needed.
- Voice: The draft still sounds compatible with the user or organization.
- Gaps: Missing facts are labeled rather than hidden.

## Final Review

When reader testing or the final quality check passes, do one last review before declaring the document done:

1. Tell the user the document appears ready from the review perspective, but they still own the final judgment.
2. Recommend that they personally re-read the document end to end.
3. Ask them to double-check facts, links, names, dates, metrics, technical details, and commitments.
4. Ask whether the document achieves the impact they wanted for the target audience.
5. Offer one more focused review if they want it; otherwise, treat the document as complete.

If the user wants one more review, focus only on final-readiness issues:

- Confusing or unsupported claims.
- Broken flow, repeated points, or missing transitions.
- Unclear decisions, asks, owners, or next steps.
- Facts, examples, or links that still need verification.
- Content that belongs in an appendix instead of the main document.

Do not reopen broad brainstorming during final review unless the user explicitly wants to change direction.

## Output Guidelines

- Keep collaboration visible: explain what you changed and why when revising.
- Use headings and bullets when they improve scanability.
- Avoid over-polishing early drafts; preserve room for user direction.
- Offer 2-3 wording options only for high-leverage sentences, titles, or framing decisions.
- Do not invent citations, metrics, names, deadlines, or commitments.

## Validation

Before finishing:

- Re-read the latest draft from the target reader's perspective.
- Identify any remaining `[TODO]`, `[Assumption]`, or `[Needs confirmation]` markers.
- Confirm that the final output matches the requested format.
- If editing an existing file, report the file path and summarize the substantive changes.
