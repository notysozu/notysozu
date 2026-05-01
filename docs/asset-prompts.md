# Asset Prompts

These prompts are for regenerating or extending the local SVG identity system. Keep the visual concept consistent: **Campus-to-Cloud Blueprint**.

## `assets/svg/banner-campus-to-cloud.svg`

Create a dark GitHub-profile hero SVG for Sonu Kumar Suman, GitHub handle `notysozu`. Use a clean engineering blueprint grid, strong contrast, and a route that reads `campus -> signal -> model -> interface -> cloud`. Include readable text for the name and motif. Use modular route nodes, subtle glow, no external fonts, no raster images, no scripts, and no tiny decorative text.

## `assets/svg/identity-grid.svg`

Create a compact dark-mode SVG panel with 3 to 5 identity modules for an AI-native product engineer. Required modules: AI-native, full-stack, product-minded, human-centred, ship / iterate. Use a blueprint grid, small cards, high-contrast labels, and restrained accent colours. Make it editable by hand with clear group IDs.

## `assets/svg/project-map.svg`

Create a dark blueprint SVG diagram showing how systems move from real-world signals to AI/model layer, interface layer, backend/cloud layer, and useful software/output. Use the repeating metaphor `campus -> signal -> model -> interface -> cloud`. Keep labels readable at GitHub README width. Avoid external icons, stock imagery, and visual noise.

## `assets/svg/footer-wave.svg`

Create a calm footer SVG that closes the campus-to-cloud route. Use a dark blueprint grid, one soft route-inspired line, a few node markers, and no heavy text. The footer should work as a quiet visual ending below the README content.

## Colour Adaptation Notes

Default palette:

- Background: `#0D1117`
- Primary text: `#E6EDF3`
- Muted text: `#8B949E`
- Accent violet: `#7C3AED`
- Accent cyan: `#06B6D4`
- Accent green: `#22C55E`
- Accent orange: `#F59E0B`

If `{{COLOUR_PALETTE}}` is provided, adapt accents first and keep the background close to GitHub dark mode unless the new palette still meets contrast requirements. Avoid one-note palettes; keep at least two accent families visible across route nodes.

## Accessibility Notes

- Every non-decorative SVG in `README.md` needs meaningful alt text.
- Decorative closers can use empty alt text in Markdown or HTML.
- Do not rely on colour alone; pair route colours with labels, shapes, or position.
- Keep text above 12 px equivalent inside SVGs.
- Preserve contrast between text and dark backgrounds.

## Export Notes

- Keep SVGs inline and hand-editable.
- Use a responsive `viewBox`.
- Avoid external images, scripts, remote fonts, and embedded base64 payloads.
- Optimise only after manual review; do not minify away useful IDs.
- Keep file size reasonable for GitHub README rendering.

## Manual Editing Tips

- Update text inside grouped layers such as `copy`, `nodes`, `modules`, and `project-layers`.
- When changing the route, adjust both the solid path and dashed overlay together.
- Reuse the same node order everywhere: campus, signal, model, interface, cloud.
- If adding a new project visual, connect it back to the route metaphor instead of adding a separate theme.
- Preserve placeholders such as `{{PREFERRED_TONE}}` when source values are not available.
