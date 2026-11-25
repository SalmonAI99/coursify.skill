# Coursify Skills

Installable, user-facing agent skills for planning, creating, and managing courses in Coursify. Each skill lives under [`skills/`](skills/) in its own directory containing a `SKILL.md` with Agent Skills-compatible YAML frontmatter (`name` and `description`) followed by workflow instructions.

## Install in an AI agent

Install these skills with the community [`skills` CLI](https://skills.sh/), which supports mainstream coding agents including Claude Code, Codex, Cursor, and others. From a project directory, run:

```bash
# Browse the available Coursify skills and choose which agent(s) to configure
npx skills add SalmonAI99/coursify.skill

# Or install all skills into one agent
npx skills add SalmonAI99/coursify.skill --skill '*' --agent claude-code

# Install just one skill into Codex
npx skills add SalmonAI99/coursify.skill --skill course-planning --agent codex

# Install all skills globally for all supported agents
npx skills add SalmonAI99/coursify.skill --skill '*' --agent '*' --global
```

Omit `--agent` to choose agents interactively. Use `--list` to inspect skills before installing, or `npx skills update` to update installed skills. The CLI installs into the current project by default; `--global` installs for your user account. See the [skills CLI documentation](https://github.com/vercel-labs/skills) for supported agents and options.

## Course planning and authoring

- [`course-planning`](skills/course-planning/SKILL.md) — clarify goals, audience, scope, constraints, and format; obtain confirmation of the brief before outlining.
- [`hierarchy-design`](skills/hierarchy-design/SKILL.md) — design or revise a course outline with live outline tools and verify changes.
- [`outline-addition`](skills/outline-addition/SKILL.md) — add modules and nested topics to the active course.
- [`outline-ordering`](skills/outline-ordering/SKILL.md) — reorder sibling items without changing the hierarchy.
- [`outline-deletion`](skills/outline-deletion/SKILL.md) — remove an explicitly selected outline subtree with scope checks.
- [`educational-writing`](skills/educational-writing/SKILL.md) — write one approved module as structured, typed lesson content.
- [`mathematical-explanation`](skills/mathematical-explanation/SKILL.md) — produce rigorous mathematical explanations in the supported lesson schema.
- [`diagram-generation`](skills/diagram-generation/SKILL.md) — create a schema-valid diagram only when it materially helps explain content.
- [`exercise-generation`](skills/exercise-generation/SKILL.md) — create objective-aligned practice and review criteria.
- [`presentation-design`](skills/presentation-design/SKILL.md) — create a structured presentation from course content using approved presentation tools.

## Website and integration skills

- [`coursify-web-workspace`](skills/coursify-web-workspace/SKILL.md) — navigate and manage courses through the Coursify website UI.
- [`coursify-web-course-editor`](skills/coursify-web-course-editor/SKILL.md) — edit outlines, lesson blocks, and presentations through the website while protecting user work.
- [`coursify-web-course-settings`](skills/coursify-web-course-settings/SKILL.md) — update course title/description/difficulty or safely delete a course.
- [`coursify-mcp-access`](skills/coursify-mcp-access/SKILL.md) — set up and safely use Coursify's read-only MCP connection.

## Important capability boundary

Coursify's in-app agent has scoped tools to read/edit outlines and lesson blocks and to create structured presentations. A separate browser/UI integration is required for an external agent to click through the website; if it is unavailable, guide the learner rather than claiming UI actions. The external MCP server is currently **read-only** and exposes `list_courses`, `get_course_outline`, and `read_lesson`; it does not create or edit website content. Do not claim that an MCP call or ordinary chat changed the website. Use the live Coursify agent tools when available, or guide the learner through the browser UI and have them confirm the result.

Course-planning and authoring skills are adapted from the Coursify v2 `.agents/skills/` catalog. The canonical in-app copies remain in that app repository; this standalone repository packages the user-facing copies for distribution and use by other agents.
