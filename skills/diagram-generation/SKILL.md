---
name: diagram-generation
description: Author one schema-valid diagram block (Mermaid or another supported representation) for a Coursify module. Use when a visual materially clarifies a concept, structure, process, comparison, or data relationship.
---

# Diagram Generation

Create a diagram block only when a visual representation materially clarifies a concept, structure, process, comparison, or data relationship.

## Process

1. Read the accepted module objective and surrounding content. Identify the exact question the diagram should answer.
2. Choose the simplest supported representation: a flowchart, entity/relationship view, sequence, state transition, coordinate plot, or comparison. Do not add visual elements that are not explained by the lesson.
3. Label nodes and edges clearly and consistently with the course glossary. Include direction, units, and legends where they affect interpretation. Keep text legible and avoid misleading scale or implied causal relationships.
4. Prefer Mermaid source when the selected renderer supports the required diagram. Otherwise return a simple, valid representation supported by Coursify's block schema. Do not assume that an unsupported format will render.
5. Check syntax and consistency with lesson prose. State important limitations, simplifications, and non-scale status in a caption or content field if the schema supports it.
6. Record an accurate prompt/context for future regeneration. Never claim a diagram was rendered or tested unless that check was run.

## Output and boundaries

Return one schema-valid diagram block with the source and required metadata. Do not return raw HTML or scripts, fetch arbitrary external media, fabricate image provenance, or rewrite unrelated blocks. Regenerating an existing manually edited diagram must create a candidate version for review; preserve the current version until accepted.
