# Porsche 911 Cabriolet — Animated Website

`index.html` is a complete single-file scroll-animated website (built with the
`animated-website` skill design system): scrolling plays the rear-to-front pan
video frame-by-frame on a canvas with a scroll-dwell engine that "almost stops"
at six content sections (hero, vision, engineering, equipment, heritage, outro),
plus a fixed glass header with crest + wordmark and mobile menu, ambient
particles, film grain, vignette, scroll progress bar, custom cursor,
glass-morphism stat cards, chapter markers, letter-split hero, an italic
marquee strip, the "Power Meets Precision" film autoplaying mid-site with
sound/play controls, a swipeable stills rail captured live from that film, an
editorial 4-column gallery mixing pan + film frames with a full lightbox
(keyboard + swipe navigation), and a crest-video CTA section.

Featured videos (hosted on Bunny CDN):

- Pan: https://sterlingcdn.b-cdn.net/porsche911/porsche-view-around.mp4
- Film: https://sterlingcdn.b-cdn.net/porsche911/the%20PORSCHE%20911%20SterlingHulk%20Power%20Meets%20Precision.mov
- Crest: https://sterlingcdn.b-cdn.net/porsche911/porschelogovideo.mp4

Note: the film is a .mov container. Chrome/Safari/Edge play H.264 MOVs, but
Firefox and some Android browsers may not — re-encoding to .mp4 (H.264/AAC)
is recommended for full coverage.

Frames are extracted client-side at load (hidden video → seek → WebP in-memory
frames), so no pre-extracted frame folder is needed; if the canvas can't capture
frames (e.g. CORS-restricted host), the site falls back to scrubbing the video
element directly. The CDN must support HTTP Range requests (Bunny does).

Tuning (in `CONFIG` inside `index.html`): scroll length is the `#anim` height
(650vh), smoothing is `LERP` (0.09), pause strength/width are `DWELL_PEAK` /
`DWELL_WIDTH`, and section positions are `DWELL_CENTERS` + each overlay's
`data-show-at` / `data-hide-at`.

---

# Original asset generation notes

AI-generated hero video for the animated website: a slow cinematic pan that starts
behind the 911 Cabriolet and arcs around to the front, revealing the landscape
around the car. Generated with the Higgsfield MCP (Seedance 2.0, 1080p, 10 s, silent).

## Files

- `index.html` — demo hero section that plays the video full-bleed as an animated
  background (`autoplay muted loop playsinline`), with the start frame as poster.

## Generated assets (hosted on Higgsfield CDN)

| Asset | URL |
|---|---|
| Video (1920x1080 MP4, 10 s) | https://d8j0ntlcm91z4.cloudfront.net/user_2vQdbkYJJTfppgV7PaStt9K0SSy/hf_20260706_063300_8dda1fc5-3cbb-430d-88b2-13ab41850007.mp4 |
| Start keyframe (rear view) | https://d8j0ntlcm91z4.cloudfront.net/user_2vQdbkYJJTfppgV7PaStt9K0SSy/hf_20260706_063103_3f727e90-7c57-4e0c-96da-f8c0a079bf6d.png |
| End keyframe (front view) | https://d8j0ntlcm91z4.cloudfront.net/user_2vQdbkYJJTfppgV7PaStt9K0SSy/hf_20260706_063208_a505ffbd-b433-41da-8884-6f52799ed74f.png |

Higgsfield job IDs (for regeneration or upscaling):

- Video: `8dda1fc5-3cbb-430d-88b2-13ab41850007`
- Rear keyframe: `3f727e90-7c57-4e0c-96da-f8c0a079bf6d`
- Front keyframe: `a505ffbd-b433-41da-8884-6f52799ed74f`

## Self-hosting the video

For production, download the MP4 and serve it from your own host so the site
doesn't depend on the Higgsfield CDN:

```bash
curl -o assets/porsche-911-pan.mp4 "https://d8j0ntlcm91z4.cloudfront.net/user_2vQdbkYJJTfppgV7PaStt9K0SSy/hf_20260706_063300_8dda1fc5-3cbb-430d-88b2-13ab41850007.mp4"
```

Then update the `<source src>` (and `poster`) in `index.html` to the local paths.

## Crest exploded-view animation

`crest.html` — second hero demo: the metallic gold Porsche crest on pure black
slowly disassembles into a floating 3D exploded view (Apple-style product
animation). Generated with Seedance 2.0 (1080p, 10 s, silent) from a Nano Banana
Pro start frame.

| Asset | URL |
|---|---|
| Crest video (1920x1080 MP4, 10 s) | https://d8j0ntlcm91z4.cloudfront.net/user_2vQdbkYJJTfppgV7PaStt9K0SSy/hf_20260706_064241_271d1f41-e0b8-4d89-8e72-a7b2adad801c.mp4 |
| Crest start frame | https://d8j0ntlcm91z4.cloudfront.net/user_2vQdbkYJJTfppgV7PaStt9K0SSy/hf_20260706_064159_f8c1966f-808f-40df-b3b2-bc023233d262.png |

Job IDs — video: `271d1f41-e0b8-4d89-8e72-a7b2adad801c`, start frame: `f8c1966f-808f-40df-b3b2-bc023233d262`.

## How it was made

1. Rear three-quarter keyframe generated with Nano Banana Pro from a text prompt
   matching the reference shots (pale chartreuse 992 Cabriolet, top down, modern
   villa, Mediterranean hills, late-afternoon light).
2. Front three-quarter keyframe generated from the rear keyframe as an image
   reference to keep the car, scene, and grade consistent.
3. Seedance 2.0 image-to-video with the rear frame as `start_image` and the front
   frame as `end_image`, prompted for a single slow gimbal orbit with no cuts.
