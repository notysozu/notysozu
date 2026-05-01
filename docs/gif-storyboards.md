# GIF Storyboards

Animated GIF files were not generated in this pass. This document gives production-ready storyboards, dimensions, timing, captions, and commands for creating them later from exported frames.

## Recommended Dimensions

- Hero GIF: `1200x420`
- Project demo GIF: `1200x520`
- Contribution/build rhythm GIF: `1200x360`
- Mobile-safe crop check: `720x420`
- Target frame rate: `12 fps` for smooth route motion without large files

## Hero GIF Storyboard

Purpose: animate the Campus-to-Cloud Blueprint without overwhelming the README.

| Frame range | Duration | Visual | Caption |
| :--- | :--- | :--- | :--- |
| 001-012 | 1.0s | Dark blueprint grid fades in. | Campus signal detected |
| 013-030 | 1.5s | Campus node lights up, then route moves toward signal. | From campus friction |
| 031-048 | 1.5s | Signal node pulses, small waveform appears. | Into structured signal |
| 049-066 | 1.5s | Model node activates with cross-lines. | Model the pattern |
| 067-084 | 1.5s | Interface card draws in. | Design the decision |
| 085-102 | 1.5s | Cloud node appears and route completes. | Ship the useful layer |
| 103-120 | 1.5s | Full banner settles on the static composition. | campus -> signal -> model -> interface -> cloud |

Animated SVG fallback: animate the route path with `stroke-dasharray` and `stroke-dashoffset`, then pulse each node with CSS keyframes. Keep a static `<svg>` fallback for GitHub clients that do not animate.

## Project Demo GIF Storyboard

Purpose: show how a featured system should be presented without inventing missing project outcomes.

| Frame range | Duration | Visual | Caption |
| :--- | :--- | :--- | :--- |
| 001-018 | 1.5s | Empty blueprint project map with three placeholder project lanes. | Choose the signal |
| 019-036 | 1.5s | Lane 1 expands: problem, stack, open/demo placeholders. | Define the system |
| 037-054 | 1.5s | Model layer and interface layer connect. | Shape the workflow |
| 055-072 | 1.5s | Backend/cloud layer appears with API path. | Carry the load |
| 073-090 | 1.5s | Output module receives the route. | Make it useful |
| 091-108 | 1.5s | Three project cards settle side by side. | Repeat the pattern |

Suggested overlay labels should use the real project data when available:

- `{{KEY_PROJECT_1_NAME}}`
- `{{KEY_PROJECT_2_NAME}}`
- `{{KEY_PROJECT_3_NAME}}`

## Contribution / Build Rhythm GIF Storyboard

Purpose: turn contribution activity into a quiet build diary, not a vanity metric.

| Frame range | Duration | Visual | Caption |
| :--- | :--- | :--- | :--- |
| 001-020 | 1.6s | Contribution grid appears as low-contrast blueprint blocks. | Small notes |
| 021-040 | 1.6s | A route line passes across selected cells. | Fixes and experiments |
| 041-060 | 1.6s | A few cells brighten in green/cyan/violet. | Systems taking shape |
| 061-080 | 1.6s | Route reaches a cloud node. | Shipped learning |
| 081-096 | 1.3s | Static end frame for loop stability. | Build diary |

Use the generated SVG at `./output/github-contribution-grid-snake-dark.svg` as the static fallback in the README.

## Static Fallback Strategy

- Keep the current local SVGs as the primary visual identity.
- Use animated assets only when they add story, not decoration.
- If a GIF is larger than 2 MB, prefer animated SVG or a static SVG.
- Always keep meaningful alt text for non-decorative animated assets.

## FFmpeg Commands

Create a palette for a clean GIF:

```bash
ffmpeg -y -framerate 12 -i frames/hero-%03d.png -vf "scale=1200:-1:flags=lanczos,palettegen" build/hero-palette.png
```

Render the hero GIF:

```bash
ffmpeg -y -framerate 12 -i frames/hero-%03d.png -i build/hero-palette.png -lavfi "scale=1200:-1:flags=lanczos[x];[x][1:v]paletteuse=dither=bayer:bayer_scale=3" assets/gif/campus-to-cloud-hero.gif
```

Render a project demo GIF:

```bash
ffmpeg -y -framerate 12 -i frames/project-%03d.png -vf "scale=1200:-1:flags=lanczos,fps=12" build/project-demo.mp4
ffmpeg -y -i build/project-demo.mp4 -vf "palettegen" build/project-palette.png
ffmpeg -y -i build/project-demo.mp4 -i build/project-palette.png -lavfi "paletteuse=dither=sierra2_4a" assets/gif/project-demo.gif
```

## ImageMagick Commands

Create a lightweight GIF from PNG frames:

```bash
magick -delay 8 -loop 0 frames/hero-*.png -layers Optimize assets/gif/campus-to-cloud-hero.gif
```

Resize and optimise an existing GIF:

```bash
magick assets/gif/campus-to-cloud-hero.gif -coalesce -resize 1200x420 -layers Optimize assets/gif/campus-to-cloud-hero.optimised.gif
```

Extract a static fallback frame:

```bash
magick assets/gif/campus-to-cloud-hero.gif[119] assets/gif/campus-to-cloud-hero-fallback.png
```
