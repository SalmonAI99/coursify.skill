---
name: outline-addition
description: Add modules, lessons, or subtopics to the active Coursify course outline with the coursify_* tools, reading the outline first and verifying writes. Use when the learner asks to build or extend the outline.
---

# Course Outline Addition

Create and persist outline items in the active Coursify course when the learner asks to build or extend its outline.

Use the hierarchy-design skill to choose scope and sequence.

## Workflow

1. Call `coursify_get_outline` first. Use its returned node IDs and parent relationships; never invent IDs or replace the root.
2. For a course-level module, call `coursify_add_outline_item` with its title and no `parent_id`. The tool adds it below the course root and returns its ID.
3. For nested lessons or subtopics, add each parent before its children, using the returned parent ID. Keep siblings in the intended learning order as you add them.
4. Follow the learner's brief and hierarchy-design guidance. Add only requested or clearly implied structure; do not generate lesson content or claim the learner confirmed assumptions.
5. Call `coursify_get_outline` again after writes. Confirm the persisted structure and summarize any assumptions.

Keep titles concise, distinct, and within the tool's 200-character limit. Do not delete existing items or restructure unrelated branches while adding.
