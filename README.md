# Porsche 911 Cabriolet — Animated Hero Video

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

## How it was made

1. Rear three-quarter keyframe generated with Nano Banana Pro from a text prompt
   matching the reference shots (pale chartreuse 992 Cabriolet, top down, modern
   villa, Mediterranean hills, late-afternoon light).
2. Front three-quarter keyframe generated from the rear keyframe as an image
   reference to keep the car, scene, and grade consistent.
3. Seedance 2.0 image-to-video with the rear frame as `start_image` and the front
   frame as `end_image`, prompted for a single slow gimbal orbit with no cuts.
