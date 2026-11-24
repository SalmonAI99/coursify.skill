---
name: presentation-design
description: Design a clear, audience-appropriate Coursify presentation from approved course content, with a coherent story, concise slides, examples, exercises, and safe structured visual components. Use when the learner asks to create or revise a presentation or slide deck.
---

# Presentation design

Create a presentation as a structured `AgentDeckSpec` using `coursify_create_presentation`. Never write raw Slidev source, Vue templates, HTML, imports, or scripts in the tool arguments.

## Before creating

1. Read the course outline with `coursify_get_outline` and the relevant lesson blocks with `coursify_get_module_content`.
2. Respect the current session scope. In a module session, create only for the active module or its descendants; do not create course-wide decks.
3. If audience, goal, or presentation length is genuinely unclear and materially changes the deck, ask one concise question. Otherwise proceed using confirmed course context and mention any reasonable assumption.
4. Make the deck teach, not merely summarize. Choose a narrative, explain unfamiliar terms, sequence from concrete examples to abstractions, and include a short practice/check slide when appropriate.

## Deck structure

- Use a specific, informative title and a concise subtitle.
- Keep each slide to one main idea and a descriptive title.
- Prefer short, readable text, examples, diagrams, tables, or comparisons over dense paragraphs.
- Preserve technical accuracy and course terminology. Do not invent data, citations, or claims.
- Include worked examples for procedural or quantitative topics; include assumptions and units.
- Add a final recap and a learner action, question, or next step.
- Use speaker notes (`prompt` on a slide block) for concise delivery cues, caveats, or elaboration not needed on the slide.

## Supported block shapes

Use blocks with `block_type` and a `content` object:

- `markdown`: `{ "markdown": "..." }`
- `latex`: `{ "tex": "..." }`
- `code`: `{ "code": "...", "language": "python" }`
- `diagram`: `{ "source": "...", "format": "mermaid" }`
- `image` / `video`: `{ "src": "https://...", "alt": "..." }` (only use a known, appropriate URL; do not fabricate one)

Do not include HTML or Vue in Markdown. The compiler escapes it. Do not place raw Slidev separators/frontmatter in block content.

## Approved physics visuals

A slide may specify one `visual`, which is rendered by a built-in, reviewed component:

- Projectile: `{ "kind": "projectile", "initial_speed": 20, "angle_deg": 45, "gravity": 9.81 }`. Defaults are in SI units. Use values that illustrate the concept and explain assumptions such as no air resistance.
- Pendulum: `{ "kind": "pendulum", "length_m": 1.5, "initial_angle_deg": 25 }`. The component uses the small-angle period model; state when that approximation is relevant.

Never invent other `kind` values or component names. The server validates ranges and builds the approved component files into the deck.

## After creating

Before replacing an existing deck, call `coursify_list_presentations` and preserve its intent unless the learner requested a replacement. Agent-authored structured specs can be replaced as a whole; manual Slidev source overrides must be reset by the learner in the presentation editor first.

The tool returns the deck ID, scope, URL, and build status/error. If the build is queued, tell the learner it is processing and point to the deck management page. If Slidev is unavailable, the structured deck spec is saved; explain the setup requirement and do not claim it is ready. If rebuilding an existing deck, preserve the learner's intent, and replace the complete structured spec deliberately rather than silently discarding authored content.
