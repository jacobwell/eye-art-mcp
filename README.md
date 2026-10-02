# Eye.Art Polyphemus MCP connector

Eye.Art Polyphemus is one conversational image-making MCP endpoint. It routes image creation, focused edits, artist-led directions, page-matched visuals from code, editable SVG, prompt ideas, and supported motion through a private workflow layer. This repository contains connection documentation only; it does not include the hosted workflow implementation.

## Connect

- Transport: Streamable HTTP
- MCP URL: `https://eye.art/api/eye-mcp`
- Authentication: none; do not send an authorization header or API key
- Full API guide: <https://eye.art/polyphemus/api>

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

Use your client's remote MCP or Streamable HTTP setup if it does not accept this JSON format directly.

## What it can do

- Create raster images with Polyphemus or an artist muse.
- Edit a supplied PNG, JPEG, or WebP while carrying image and conversation context.
- Match visuals to a page by supplying relevant HTML, CSS, JavaScript, JSX, TSX, or TypeScript.
- Return editable SVG markup for icons, line art, diagrams, and flat scenes.
- Offer three varied prompt ideas and route supported motion requests.
- Continue conversations and poll asynchronous image jobs.

## Available tools

- `eye_art_make_image` — image, artist-led, page-match, small-art, and supported motion requests.
- `eye_art_edit_image` — focused edits to an attached source image.
- `eye_art_make_svg` — editable SVG source; generation is synchronous.
- `eye_art_prompt_ideas` — three varied prompt directions.
- `eye_art_image_status` — poll an image or edit job until it completes or fails.
- `eye_art_create_session` — create a private anonymous session for saved-chat management.
- `eye_art_list_conversations` — list conversations for a session.
- `eye_art_get_conversation` — read a conversation transcript.
- `eye_art_delete_conversation` — delete a conversation and its stored references.

## Keep chat context

Pass the returned `conversationId` on follow-up image or edit calls to preserve the chat and its saved image references. To manage saved chats, first call `eye_art_create_session`, then pass its returned `sessionId` to the list/get/delete tools. Treat `sessionId` as a private anonymous capability; do not publish or share it. Attach a new reference when you want to change the active source image.

Image and edit calls may return asynchronous jobs. Poll each returned job with `eye_art_image_status`; some staged workflows may take around ten minutes. SVG generation returns source synchronously.

## References and limits

Send image references as PNG, JPEG, or WebP data URLs; Eye.Art does not fetch arbitrary image URLs. For page matching, include only the relevant HTML/CSS/code in `pageReferences`. MCP request bodies are limited to 12 MB; each reference image is limited to 2 MB and references together to 6 MB. Anonymous image generation is limited to 20 requests per hour per caller network identity.

Prompts, references, outputs, and conversation data are retained for 30 days. Do not send sensitive source material unless you intend it to be processed by the hosted service. Artist names describe visual direction and do not imply endorsement or affiliation with the artist or estate.
