# Eye.Art Polyphemus

Use the `eye-art` MCP tools when the user asks to create or edit an image, make
editable SVG art, match a website's visual style, or explore a supported motion
workflow.

- Use `eye_art_make_image` for raster images and site-matched visuals.
- Use `eye_art_edit_image` when changing an existing image; include the source
  image and preserve the requested subject and composition unless asked to
  change them.
- Use `eye_art_make_svg` when the user wants editable vector source.
- Use `eye_art_prompt_ideas` when the user wants inspiration or prompt options.
- Keep the returned `conversationId` for follow-up requests and reuse it so the
  server can retain image and chat context. Poll `eye_art_image_status` for
  queued jobs instead of starting duplicate generations.

The endpoint is free to try and requires no API key. Prompts, references,
outputs, and conversation data may be retained for up to 30 days. Do not send
private source material unless the user intends it to be processed by the
hosted service. Artist names communicate visual direction and do not imply
endorsement.
