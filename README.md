# FishCoach assets

Large files for the [FishCoach](https://github.com/Fishy68/fishy) Android app, kept out of the APK and downloaded by the app when needed.

| Path | What | Used for |
|---|---|---|
| `photos/<species id>.webp` | 732 species photos, up to 720 px | Full-size photos on species pages. The app ships small thumbnails and fetches these on demand, then caches them. |
| `fishid/dinov2_small_q.onnx` | DINOv2-small image encoder, int8-quantised ONNX (24 MB) | "Identify a fish". Downloaded the first time it's used and checked against `manifest.json`. |
| `manifest.json` | Version, the model's SHA-256 and size, and the photo count | Integrity check before the app uses a download. |
| `photo_credits.json`, `CREDITS.md` | Author, license and source of every photo | Attribution. The app shows the same credits in Settings. |

The app reads these files at a fixed commit (its `ASSETS_URL` build setting ends in the commit hash), so later changes to `main` never break an installed version. To publish a new set, commit it here, then point `ASSETS_URL` in the app's build at the new commit and update the model hash there if the model changed.

## Licenses

- **Photos**: freely licensed images from Wikimedia Commons, iNaturalist and Openverse, restricted to licenses that allow commercial use (CC0, public domain, CC BY and CC BY-SA). Each photo keeps its own license; see `CREDITS.md`.
- **Model**: DINOv2 by Meta AI, Apache License 2.0 (https://github.com/facebookresearch/dinov2). Converted to ONNX and quantised to int8; weights otherwise unchanged.
