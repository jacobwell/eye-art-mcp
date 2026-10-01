# Connect an agent to Eye.Art Polyphemus

Add this remote MCP server in a client that supports Streamable HTTP:

- Name: `eye-art`
- URL: `https://eye.art/api/eye-mcp`
- Transport: Streamable HTTP
- Authentication: none; omit authorization headers and API keys

Use `eye_art_make_image` for raster art, `eye_art_edit_image` when changing a
provided image, and `eye_art_make_svg` when the user needs editable vector
source. Send image references as PNG, JPEG, or WebP data URLs. For web visuals,
include the relevant HTML/CSS snippets with `eye_art_make_image` in
`site_match` mode. Keep the returned `conversationId` and pass it to follow-up
calls so the server can preserve conversation and reference context. Poll
`eye_art_image_status` for a job returned by a long-running image or edit call.

The complete tool contract, examples, limitations, and data-retention details
are documented at <https://eye.art/polyphemus/api>.
