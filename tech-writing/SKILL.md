---
name: tech-writing
description: Draft, rewrite, review, and structure technical content so it is clear, concise, reader-first, accessible, evidence-backed, and action-oriented. Use when Codex needs to write or improve documentation, README files, design docs, API docs, tutorials, onboarding guides, release notes, specs, comments, CLI help, support content, or Chinese technical prose that needs evidence-first reasoning, less filler, and fewer buzzwords.
license: MIT
---

# Tech Writing

## Overview

Apply practical technical writing principles with one goal: help the target reader understand something quickly and take the right action. Prefer simple wording, explicit structure, consistent terminology, accessible presentation, and concrete examples.

For Chinese technical prose that needs evidence-first reasoning, less filler, or buzzword cleanup, load `references/chinese-technical-prose.md`.

## Workflow

1. Identify the reader and outcome.
- Infer who the reader is, what they already know, and what they need to do after reading.
- State the purpose early. Narrow the scope if the request is broad.

2. Choose the right document shape.
- Use task-oriented structure for how-to content.
- Use concept -> key points -> examples for explanatory content.
- Use reference structure for APIs, commands, flags, schemas, and limits.
- Use tables only when comparison is faster than prose.

3. Draft for clarity.
- Prefer common words over jargon unless the technical term is required.
- Prefer active voice.
- Keep sentences short. Split stacked clauses.
- Use precise verbs and concrete nouns.
- Keep pronouns unambiguous. Repeat the noun if needed.
- Use one term for one concept throughout.
- For strong claims, show the evidence, observation, metric, trace, example, or constraint that supports the conclusion.

4. Organize for scanning.
- Start sections and paragraphs with the main point.
- Use informative headings that describe a task or takeaway.
- Convert dense enumerations into lists.
- Keep list items parallel in structure.
- Put prerequisites, limits, and caveats before the reader hits them.

5. Make examples earn their length.
- Use the smallest realistic example that proves the point.
- Explain why the example matters when it is not obvious.
- Avoid long sample code with irrelevant setup.
- Include anti-examples only when they clarify a likely mistake.

6. Make the content accessible.
- Avoid color-only references such as "click the red button."
- Use meaningful link text.
- Write alt text for informative images.
- Use inclusive language.
- Avoid dense screenshots or diagrams that are not explained in text.

7. Write helpful error messages when relevant.
- Explain what failed.
- Explain why, if known.
- Tell the user exactly how to fix it.
- Name the invalid value, required format, limit, or conflicting state.
- Keep the tone neutral and direct.

8. Edit aggressively.
- Remove filler, throat-clearing, and repeated context.
- Check that each paragraph has one clear job.
- Verify terms, commands, filenames, flags, and examples.
- Cut any sentence that does not help the reader decide or act.
- In Chinese technical prose, delete narrator-style transition sentences that only announce the writing flow.

## Default Output Pattern

For new documents, prefer this order:

1. Title
2. One-sentence summary
3. Audience or prerequisites
4. Main sections in reader task order
5. Examples
6. Edge cases or troubleshooting
7. Links to deeper reference material

## Rewrite Heuristics

- Replace "allows you to" with the verb.
- Replace abstract nouns with actions.
- Replace "simply", "just", "obviously", or "easy" with concrete instruction or remove them.
- Replace long lead-ins with the point.
- Replace passive constructions when the actor matters.
- Define acronyms on first use unless the audience clearly already knows them.
- Replace unsupported Chinese buzzwords or empty evaluative words with specific actors, actions, constraints, data, or effects.

## Review Checklist

- Can the target reader understand the first paragraph without extra context?
- Does each heading help someone scan to the right section?
- Are terms consistent?
- Are commands, paths, and identifiers exact?
- Does each example earn its length?
- Are prerequisites and constraints explicit?
- Are strong claims backed by evidence or clearly marked as assumptions?
- For Chinese prose, are buzzwords, empty evaluations, and narrator-style transition sentences removed?
- If there is an error state, does the text explain recovery?
- Would this still work for a reader using assistive technology?

## Response Modes

- Draft: produce the requested document directly.
- Rewrite: preserve meaning and improve clarity and structure.
- Review: identify ambiguity, missing context, structural problems, and weak examples before suggesting edits.
- Condense: keep substance and remove redundancy.
- Expand: add missing prerequisites, examples, caveats, or recovery steps without bloating.

## Style Guardrails

- Prefer concise, production-friendly wording.
- Do not over-explain obvious engineering basics to expert readers.
- Do not add marketing tone unless the user asks.
- Do not invent facts, APIs, constraints, or examples.
- If information is missing, make the gap explicit or ask one focused question.

## References

- `references/chinese-technical-prose.md`: use for Chinese technical prose that needs evidence-first reasoning, narrator-style filler removal, and buzzword or empty-word cleanup.
