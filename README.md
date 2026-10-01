# Eye.Art Polyphemus MCP connector

Polyphemus is Eye.Art's no-key, hosted image-making MCP. Connect to the remote
server; there is no local service to install and this package does not contain
the private workflow implementation.

## Connect

- Transport: Streamable HTTP
- MCP URL: `https://eye.art/api/eye-mcp`
- Authentication: none
- Website and guide: <https://eye.art/polyphemus/api>

Example generic client configuration:

```json
{
  "mcpServers": {
    "eye-art": {
      "url": "https://eye.art/api/eye-mcp"
    }
  }
}
```

Use your client's remote MCP / Streamable HTTP option if it does not accept
this JSON format directly. Do not add an authorization header or place an API
key in client configuration.

## What it can do

- Make artist-guided images, compact art, webpage-matched visuals, and
  supported motion requests through one image tool.
- Continue a chat with its returned `conversationId`; attached references are
  retained with that conversation for up to 30 days.
- Edit a supplied PNG, JPEG, or WebP image while keeping the source image
  attached to the request.
- Return editable SVG source for icons, line art, diagrams, and flat scenes.
- Suggest varied prompt directions and poll longer-running image jobs.

The MCP exposes these tools: `eye_art_make_image`, `eye_art_make_svg`,
`eye_art_edit_image`, `eye_art_prompt_ideas`, `eye_art_image_status`,
`eye_art_list_conversations`, `eye_art_get_conversation`, and
`eye_art_delete_conversation`. Read the linked API guide for arguments,
reference formats, examples, and limitations.

## Limits and privacy

Eye.Art is free to try without a key. Anonymous image generations are limited
to 20 per hour per caller network identity. Image prompts, references, outputs,
and conversation data are retained for up to 30 days for continuity and
service operations, then expire under the current retention policy. Do not
send private or sensitive source material unless you intend it to be processed
by the hosted service.

Artist names describe visual guidance only. Eye.Art is not affiliated with or
endorsed by the named artists or their estates. This is a hosted service; its
workflow source and provider integrations are not included in this connector
package.

## Publisher notes

This directory is intentionally endpoint-only. For a LobeHub marketplace
plugin, generate the marketplace manifest against the live server with the
official `lhm plugin init --url https://eye.art/api/eye-mcp --dir <output>`
command, review the generated tool schemas, and publish from a repository the
publisher controls. Do not hand-maintain a second copy of the live tool schema.

For clients that support `llms-install.md`, see [`llms-install.md`](./llms-install.md).

The marketplace icon is [`icon.png`](./icon.png), a square 400×400 PNG.
