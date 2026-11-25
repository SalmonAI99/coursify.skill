---
name: hierarchy-design
description: Design or revise a course hierarchy from a learner-confirmed brief, and persist outline changes in the live Coursify course with the coursify_* outline tools. Use when the learner asks to build, extend, restructure, or reorder the course outline, or wants a proposed structure to review.
---

# Hierarchy Design

Design a useful outline from the learner's course brief and stated intent. Distinguish learner-confirmed requirements from recommendations, and mark unresolved assumptions rather than presenting them as facts.

## Design principles

1. Start from an observable learning outcome. Each node should contribute to something learners can explain, decide, or do.
2. Order topics by dependencies: foundations before ideas that rely on them. Visual nesting is for navigation, not a prerequisite graph.
3. Use clear, teachable scopes. Avoid vague catch-all modules, arbitrary microtopics, and unnecessary depth.
4. Respect the audience, requested depth, time, constraints, scope, and exclusions. Do not infer mastery from self-report.
5. Use a coherent applied thread or examples where useful, but do not assume every course needs a project.
6. Do not invent citations, sources, prerequisites, or learner-confirmed preferences.

## Creating or updating the live outline

When the learner explicitly asks to build or modify the outline shown on the course homepage, use the Coursify outline tools to make the changes in the active course. Do not merely return a proposed outline in chat.

1. Call `coursify_get_outline` before writing. Preserve the course root and any existing branches the learner did not ask to replace.
2. Add top-level modules beneath the root using `coursify_add_outline_item` without `parent_id`. Add nested children only when hierarchy is useful for navigation; create a parent first and use its returned ID for children.
3. Reorder only when requested, using `coursify_move_outline_item` and verifying sibling order with a fresh read. The move operation cannot change parents.
4. Delete only when explicitly requested. Deletion removes the entire subtree; inspect descendants and clarify scope if ambiguous.
5. Read the outline again after modifications. In the final response, summarize what was persisted and mention assumptions; never claim success without tool confirmation.

A request to discuss or propose an outline is not automatically permission to overwrite existing content. Never modify lesson blocks or other course components unless a dedicated application tool explicitly supports that change.
