---
name: exercise-generation
description: Create objective-aligned practice for an approved Coursify module with reference answers and observable acceptance criteria. Use when adding, revising, or regenerating exercises, quizzes, or project checks.
---

# Exercise Generation

Create practice that tests an approved module objective and gives the learner a useful way to check their reasoning. Read the module objective, prerequisites, surrounding lesson content, learner context, and applicable course-plan constraints before writing.

## Select the exercise

Choose a form that matches the objective:

- **Explain:** ask for a causal explanation, interpretation, or comparison, not a memorized definition.
- **Predict and check:** ask the learner to record a prediction before changing or running something, then compare it with the observed result.
- **Debug:** present a plausible error and ask for its cause, repair, and prevention.
- **Build or apply:** ask for a bounded artifact, decision, or worked result with concrete acceptance criteria.
- **Objective response:** use a closed question only when one unambiguous answer is pedagogically useful; avoid answer clues from option length or wording.

Use one or a small number of focused exercises rather than adding questions to satisfy a quota. Estimate learner effort and avoid redundant checks. Include scaffolding for unfamiliar formats without giving away the solution.

## Answers and criteria

Provide a reference answer for open-ended exercises, including reasonable alternatives where applicable. Define criteria in observable terms: what must be explained, predicted, repaired, tested, or delivered. For runnable work, specify tests, assertions, or expected behavior; never claim the code was run unless it actually was. Do not grade confidence or the presence of keywords in isolation.

Keep answer material separate from the learner-facing prompt when the UI supports that separation. Do not ask the learner to supply arbitrary environment details unrelated to the objective. Respect course safety and avoid requiring external services, paid tools, or hardware unless the confirmed course plan allows them.

## Output and boundaries

Return only the exercise content shape allowed by Coursify's block contract. Keep exercises linked to their module objective and suitable for independent regeneration. Do not modify lesson blocks, course hierarchy, learner progress, or assessment results. Do not declare mastery; the product's assessment policy and learner review own that decision.
