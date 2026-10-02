# Connect an agent to Eye.Art Polyphemus

Add this remote MCP server in a client that supports Streamable HTTP:

- Name: `eye-art`
- URL: `https://eye.art/api/eye-mcp`
- Transport: Streamable HTTP
- Authentication: none; do not send an authorization header or API key

## Choose a tool

- `eye_art_make_image` creates raster art, uses an artist muse, matches a page, makes small art, or starts a supported motion workflow. For page matching, include relevant HTML, CSS, JavaScript, JSX, TSX, or TypeScript in `pageReferences`.
- `eye_art_edit_image` makes a focused change to a supplied PNG, JPEG, or WebP data URL while preserving the requested image context.
- `eye_art_make_svg` returns editable SVG markup for icons, line art, diagrams, or flat scenes. SVG generation is synchronous.
- `eye_art_prompt_ideas` returns three varied directions.
- `eye_art_image_status` checks a job returned by image creation or editing; keep polling until it completes or fails. Longer workflows may take several minutes.

## Keep chat context

Pass each returned `conversationId` to the next image or edit call to continue the chat and keep its references. To list, inspect, or delete saved chats, first use `eye_art_create_session`; keep its returned `sessionId` private, then use `eye_art_list_conversations`, `eye_art_get_conversation`, or `eye_art_delete_conversation` with that session. A session ID is a private anonymous capability, not a public identifier.

The nine available tools are `eye_art_make_image`, `eye_art_make_svg`, `eye_art_edit_image`, `eye_art_prompt_ideas`, `eye_art_image_status`, `eye_art_create_session`, `eye_art_list_conversations`, `eye_art_get_conversation`, and `eye_art_delete_conversation`.

Anonymous image generation is limited to 20 requests per hour per caller network identity. MCP request bodies are limited to 12 MB; reference images are limited to 2 MB each and 6 MB combined. Prompts, references, outputs, and conversations are retained for 30 days. Send only material you intend to process through the hosted service.

Full schemas, examples, limitations, and retention details: <https://eye.art/polyphemus/api>.
