# Deploy — Porsche 911 Cabriolet website

## Files to upload (all into the SAME folder as your videos)

Upload everything in this zip to the `porsche911` folder of the Bunny Storage
Zone behind `sterlingcdn.b-cdn.net`:

| File | Purpose |
|---|---|
| `index.html` | The entire website (all CSS/JS inline, no build step) |
| `favicon.svg` | Browser tab icon (modern browsers) |
| `favicon.ico` | Browser tab icon (fallback) |
| `og-image.jpg` | Social share card (WhatsApp / iMessage / X / Slack previews) |

## Live URL

    https://sterlingcdn.b-cdn.net/porsche911/index.html

Hosting the page next to the videos keeps everything same-origin, so the
premium frame-by-frame scroll engine works with no CORS configuration.

## The videos (already on the CDN — nothing to do)

- porsche-view-around.mp4 — scroll-driven hero sequence
- the PORSCHE 911 SterlingHulk Power Meets Precision.mov — mid-site film
- porschelogovideo.mp4 — crest CTA background

Recommended: re-encode the film `.mov` to `.mp4` (H.264/AAC) and update the
two URLs in `index.html` (search for `.mov`) — Firefox and some Android
browsers won't play MOV containers.

## Custom domain (optional)

Add a pull-zone hostname (e.g. `porsche911.yourdomain.com`) in Bunny pointing
at the same storage, and the site works there unchanged.

## Tuning

All knobs are in `CONFIG` near the top of the `<script>` in `index.html`:
scroll length (`#anim` height, 650vh), smoothing (`LERP` 0.09), pause
strength/width (`DWELL_PEAK` / `DWELL_WIDTH`), section timings
(`DWELL_CENTERS` + each overlay's `data-show-at`/`data-hide-at`), and the
gallery/stills frame picks (`GALLERY` / `STILLS` arrays).
