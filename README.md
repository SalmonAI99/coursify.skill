# Coursify Skills

Installable, user-facing agent skills for planning, creating, and managing courses in Coursify. Each skill is a directory containing a `SKILL.md` with Agent Skills-compatible YAML frontmatter (`name` and `description`) followed by workflow instructions.

## Course planning and authoring

- [`course-planning`](course-planning/SKILL.md) — clarify goals, audience, scope, constraints, and format; obtain confirmation of the brief before outlining.
- [`hierarchy-design`](hierarchy-design/SKILL.md) — design or revise a course outline with live outline tools and verify changes.
- [`outline-addition`](outline-addition/SKILL.md) — add modules and nested topics to the active course.
- [`outline-ordering`](outline-ordering/SKILL.md) — reorder sibling items without changing the hierarchy.
- [`outline-deletion`](outline-deletion/SKILL.md) — remove an explicitly selected outline subtree with scope checks.
- [`educational-writing`](educational-writing/SKILL.md) — write one approved module as structured, typed lesson content.
- [`mathematical-explanation`](mathematical-explanation/SKILL.md) — produce rigorous mathematical explanations in the supported lesson schema.
- [`diagram-generation`](diagram-generation/SKILL.md) — create a schema-valid diagram only when it materially helps explain content.
- [`exercise-generation`](exercise-generation/SKILL.md) — create objective-aligned practice and review criteria.
- [`presentation-design`](presentation-design/SKILL.md) — create a structured presentation from course content using approved presentation tools.

## Website and integration skills

- [`coursify-web-workspace`](coursify-web-workspace/SKILL.md) — navigate and manage courses through the Coursify website UI.
- [`coursify-web-course-editor`](coursify-web-course-editor/SKILL.md) — edit outlines, lesson blocks, and presentations through the website while protecting user work.
- [`coursify-web-course-settings`](coursify-web-course-settings/SKILL.md) — update course title/description/difficulty or safely delete a course.
- [`coursify-mcp-access`](coursify-mcp-access/SKILL.md) — set up and safely use Coursify's read-only MCP connection.

## Important capability boundary

Coursify's in-app agent has scoped tools to read/edit outlines and lesson blocks and to create structured presentations. A separate browser/UI integration is required for an external agent to click through the website; if it is unavailable, guide the learner rather than claiming UI actions. The external MCP server is currently **read-only** and exposes `list_courses`, `get_course_outline`, and `read_lesson`; it does not create or edit website content. Do not claim that an MCP call or ordinary chat changed the website. Use the live Coursify agent tools when available, or guide the learner through the browser UI and have them confirm the result.

Course-planning and authoring skills are adapted from the Coursify v2 `.agents/skills/` catalog. The canonical in-app copies remain in that app repository; this standalone repository packages the user-facing copies for distribution and use by other agents.
