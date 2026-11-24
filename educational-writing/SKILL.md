---
name: educational-writing
description: Write learner-facing material for one approved Coursify module as ordered chunks of typed blocks. Use when generating, expanding, or regenerating lesson content for an accepted module objective.
---

# Educational Writing

Generate course content that teaches one approved module at a time. The learner-facing material is composed of Coursify chunks and typed blocks; return only the structured output allowed by the host contract.

## Before writing

Read the accepted hierarchy, module objectives, prerequisites, course brief, learner-provided context, module prompt, and any relevant sources. Use course-wide terms consistently. If the objective, audience, prerequisites, or prompt is too ambiguous to write safely, return a clarification request or an explicit assumption rather than inventing requirements.

Do not introduce unexplained prerequisites, tools, or terminology. A learner's self-reported experience can guide explanations, but is not verified mastery. Keep the content scoped to the approved module objectives and course constraints.

## Teaching structure

Use a clear progression appropriate to the subject:

1. Motivate the idea with a concrete question, case, or practical need.
2. Explain the key terms and give a precise definition or procedure.
3. Work through a representative example, showing reasoning and intermediate steps.
4. Explain assumptions, boundaries, common errors, and a useful counterexample when relevant.
5. Provide a short application or practice prompt aligned with the objective.
6. Summarize the central result only when it helps the learner use it later.

Use a textbook-like, precise, calm style rather than marketing language or filler. Tables should express real comparisons; diagrams should explain relationships or processes. Mathematical expressions use LaTeX blocks where the content model supports them. Code should be complete enough to understand and, where appropriate, run. State relevant versions and source references when content is volatile.

## Blocks and generation

Use only supported block types and satisfy each type's content schema. Keep blocks independently understandable and regenerable; do not hide an entire lesson inside an unstructured text blob. Include a useful generation prompt/context for diagram blocks when the contract supports it. For images and media, include provenance/attribution required by the host and never invent a source or license. Do not put executable untrusted scripts into content.

Practice should test the module objective, not arbitrary recall. Explain a small exercise enough for the learner to attempt it, but do not include a full solution immediately if the exercise is intended for independent work. Use separate exercise blocks or structured questions when available. Do not claim an assessment is passed.

## Output and safety

Return a `GeneratedModule`-shaped result with a meaningful title, objectives, ordered chunks, and typed blocks. Validate every block against its per-type schema. Invalid or incomplete output must be returned as an error, not silently omitted. The server validates and persists; do not claim database writes or course publication that did not happen.

If content replaces or regenerates manually edited material, the system must create a reviewable candidate and preserve the current content until the learner accepts it. Do not encourage bypassing this safeguard.
