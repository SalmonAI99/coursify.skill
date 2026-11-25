---
name: outline-deletion
description: Remove outline items and their subtrees from the active Coursify course with the coursify_* tools after confirming scope. Use only when the learner explicitly asks to delete or remove outline items.
---

# Course Outline Deletion

Remove outline items only when the learner explicitly asks to delete or remove them.

## Workflow

1. Call `coursify_get_outline` and locate the exact target by its stable node ID. Never delete the course root.
2. Determine whether the target has descendants. Deletion removes the entire subtree, not just the selected row. If the learner's request does not clearly include those descendants, explain the impact and ask which scope they intend before deleting.
3. Call `coursify_delete_outline_item` with the target's ID. Do not delete unrelated items or recreate their content elsewhere unless requested.
4. Call `coursify_get_outline` to verify the target and intended descendants are gone. Report what was removed based on the tool results.

Do not claim deletion succeeded unless the tool confirms it. Deleting outline structure does not authorize deleting or regenerating unrelated course materials.
