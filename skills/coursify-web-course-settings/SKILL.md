---
name: coursify-web-course-settings
description: Update a Coursify course's title, description, or difficulty in the signed-in website and handle course deletion safely. Use when the learner asks to edit course metadata, review settings, or remove a course.
---

# Coursify Web Course Settings

Help the owner manage course metadata and lifecycle using the signed-in Coursify website. Use a host-provided browser/UI tool when available; otherwise guide the learner through the visible UI. Do not call undocumented endpoints or manipulate application storage directly.

## Update course details

1. Confirm the course by its visible title and open its **Course settings** panel.
2. Change only the fields requested: title, description, and/or difficulty. Do not infer a difficulty level or rewrite the learner's description without permission.
3. Submit **Save settings** and verify the updated values from the UI. If the save state is unclear, ask the learner to check the page rather than claiming success.
4. Report the exact fields changed. Preserve the course's content and outline.

## Delete a course

Deletion removes the course and all of its content. Treat it as destructive and irreversible unless the UI explicitly offers recovery.

1. Never delete based on a vague request such as “clean up my courses.” Ask which exact course they mean.
2. Confirm the exact course title and explicitly state that its outline, lessons, and associated materials will be removed.
3. Proceed only after the learner confirms deletion of that named course. Use the visible UI's confirmation step if present.
4. Verify the course is absent from the course list. If the outcome is uncertain, report uncertainty; do not retry blindly.

## Boundaries

- Course status is not proof of public visibility. Do not claim a course is published or shared unless an explicit UI control confirms that state.
- Do not change sharing, account settings, credentials, or another course as part of a metadata request.
- Do not request passwords, cookies, or tokens in chat. Treat course content as private and do not expose unrelated course data.
- Never claim an edit or deletion succeeded without UI confirmation.

## Handoff

Report the course title, the fields changed or exact deletion confirmed, the visible save/delete result, and any remaining user action.
