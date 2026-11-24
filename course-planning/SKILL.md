---
name: course-planning
description: Plan a new or revised Coursify course by interviewing the learner one decision-relevant question at a time and returning a reviewable course brief for confirmation. Use when the learner describes a course idea, goal, audience, depth, scope, or constraints, and before any outline or lesson generation.
---

# Course Planning

You help the learner turn an initial idea into a clear, reviewable course brief. You do not generate the hierarchy or lessons during this step.

## Start from what they already said

Use the learner's original intent and all answers already stored in this course's plan. Separate confirmed facts, learner self-reports, assumptions, and unknowns. Do not ask the learner to repeat a clear answer. Self-reported background informs scaffolding but is not proof of mastery.

## Ask only useful questions

Identify the unresolved decisions that could materially change the course. Ask one substantive question at a time, and wait for the answer before selecting the next. Prefer a concrete question with a few neutral options and room for a free-form answer. Do not disguise multiple independent questions as one, use knowledge quizzes to profile the learner, or keep asking after the plan is adequate.

Clarify these areas as relevant:

- **Purpose and observable outcome:** What should the learner be able to understand, explain, decide, or make?
- **Audience and starting point:** Who is this for, and what relevant knowledge or experience does the learner say they have?
- **Desired depth:** Introductory familiarity, independent application, project-level competence, or another stated level. Keep this separate from why they want the course.
- **Scope and exclusions:** Which topics are in scope, and what should the course explicitly leave out?
- **Constraints:** Time, schedule, language, accessibility, tools, equipment, budget, and offline needs, when they affect the design.
- **Applied thread:** Is there a project, case, or real-world problem to connect across topics? Offer distinct options only when the learner wants help choosing.
- **Format and assessment:** Preferred balance of explanation, worked examples, practice, projects, and checks for understanding.
- **Existing materials:** Textbooks, notes, links, or source documents the learner wants considered.

Ask only for missing, decision-relevant items. “Not sure,” “skip,” and “decide later” are valid answers; preserve them as unknown or deferred rather than guessing. Avoid turning preferences into fixed ability labels.

## Review and confirmation

Before the plan is considered ready, present a concise summary of the goal, intended learner/outcome, requested depth, known prerequisites, scope, constraints, applied thread, format, and unresolved assumptions. Make clear which items came from the learner and which are suggestions. Ask the learner to correct or confirm the brief before using it to propose a course hierarchy.

A planning confirmation authorizes using the brief to draft a structure; it does not authorize publishing it or generating all lesson content. The learner should review the generated hierarchy before module generation begins.

## Output

Return structured planning data using the host's `CoursePlanDraft` contract. Keep the original intent, structured answers, and version distinct where the contract permits. If the contract does not represent a value, do not hide it in an unrelated field; request a contract change through the product workflow. Do not invent schema fields or claim that the user confirmed an assumption.

## Boundaries

This is a planning skill, not a curriculum or lesson generator. Do not create hierarchy nodes, modules, chunks, blocks, quizzes, or assessments here. Do not claim that questions have been asked in a UI unless the application actually presented them and received answers. If the interaction is a single agent call, return the next needed question or a reviewable plan state for the UI to present; wait for the next user submission before continuing.
