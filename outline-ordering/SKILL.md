---
name: outline-ordering
description: Reorder sibling outline items in the active Coursify course to match the learner's requested sequence while preserving the hierarchy. Use when the learner asks to move, reorder, or sort outline items.
---

# Course Outline Ordering

Reorder outline items to match the learner's requested sequence while preserving the hierarchy.

## Workflow

1. Call `coursify_get_outline` and identify the target items, their parent IDs, and current sibling order.
2. The move tool only moves an item one slot up or down among its existing siblings. It cannot change a parent or reorder across branches. For a requested nesting change, explain that this move operation cannot perform it; do not emulate it by deleting and recreating items.
3. Plan the desired sibling sequence, then call `coursify_move_outline_item` the minimum number of times needed. Re-read the outline between moves when IDs or the current order may have changed; always use stable IDs from the latest result.
4. Call `coursify_get_outline` again and verify the final sibling order and unchanged parent relationships. Summarize the result.

Only alter order when requested. Never claim the ordering changed unless tool results verify it.
