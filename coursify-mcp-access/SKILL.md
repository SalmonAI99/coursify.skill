---
name: coursify-mcp-access
description: Connect an MCP-capable agent to a learner's Coursify account for read-only access to their courses, outlines, and lessons. Use when they ask to set up, validate, troubleshoot, or safely use Coursify MCP.
---

# Coursify MCP Access

Help the learner configure the Coursify Streamable HTTP MCP server for **read-only** access. The currently documented server tools are `list_courses`, `get_course_outline`, and `read_lesson`. MCP cannot create courses or modify outlines, lesson blocks, or presentations.

## Setup

1. Ask which MCP-capable client the learner uses only if their client is not already clear. Use that client's supported configuration format; do not assume every client uses the same config path or environment-variable interpolation.
2. Direct the learner to sign in to Coursify and open **Courses → MCP access** (or the current visible MCP access settings page).
3. Have the learner create a clearly named token for this client. Coursify stores only a hash and displays the plaintext token once. Tell them to copy it directly into a local secret store/environment variable and not paste it into chat.
4. Configure the client with the instance's `/mcp` Streamable HTTP URL and an `Authorization: Bearer <token>` header, using the client's documented secure secret mechanism. For a local instance, the README example uses `http://127.0.0.1:3002/mcp`; for a deployed instance require HTTPS.
5. Validate the connection using the client's MCP server/tool listing or a harmless `list_courses` call. Treat course names and returned content as private data; show only what is needed for the request.
6. Explain revocation: the learner can revoke the named token from the Coursify MCP access page. If a token was exposed, revoke it and create a replacement.

## Secure configuration

- Never ask the learner to send the token, password, cookie, or a full configuration containing secrets into chat.
- Do not commit tokens to source control or put them in browser-side JavaScript. Avoid shell history when setting secrets; prefer the client's OS credential manager or protected environment mechanism.
- Use only the Coursify instance the learner explicitly selected. Do not redirect bearer credentials to another host or endpoint.
- For remote servers, use HTTPS and verify the hostname before sending credentials. A self-hosted administrator may need to allow the public hostname in `COURSIFY_MCP_ALLOWED_HOSTS`; the server's Origin allowlist matters for browser-based MCP clients. Do not advise broad wildcard allowances.
- Keep MCP grants narrow: tokens currently grant read-only access to the authenticated user's data. Revoke tokens that are no longer needed.

## Capabilities and limits

- `list_courses`: list courses belonging to the authenticated Coursify user.
- `get_course_outline`: read a course outline after supplying a course ID.
- `read_lesson`: read lesson content after supplying the course ID and outline node ID.
- These tools do not add, edit, reorder, delete, generate, publish, or share content. Use the signed-in website UI or Coursify's in-app agent editing tools for those tasks.
- Do not invent tool arguments beyond the server schema or claim a successful connection without a client/server confirmation.

## Troubleshooting

- **Unauthorized:** check that the token was copied correctly, is sent as a Bearer header, and has not been revoked. Create a replacement if it was only displayed once and is lost.
- **No tools or connection failure:** verify the exact `/mcp` URL, that the Coursify server is running/reachable, and that the chosen client supports Streamable HTTP. Use the client's own connection diagnostics rather than guessing configuration fields.
- **Host/origin rejection:** a self-hosted operator should review the narrow `COURSIFY_MCP_ALLOWED_HOSTS` and, only for browser clients, `COURSIFY_MCP_ALLOWED_ORIGINS` settings. Do not disable host/origin protections as a shortcut.
- **Course not found:** confirm the selected course ID and that it belongs to the account represented by the token. Do not attempt to bypass owner scoping.

## Handoff

Summarize which client and server URL were configured (omit secrets), whether validation succeeded, what read-only tools are available, and any remaining setup steps. Never echo the bearer token.
