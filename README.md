# AngleLab — RULA angle measurement helper

A static, mobile-friendly web app prototype that estimates joint angles from a live camera or uploaded photo. It does **not** calculate RULA scores.

## Included
- `index.html`: complete app; no build step required.
- Uses MediaPipe Pose Landmarker and Hand Landmarker from CDN.
- Intended to be hosted as a static HTTPS website.

## Run locally
Because browser camera access requires a secure context, use localhost rather than opening the file directly:
1. Install Python 3 if needed.
2. In this folder run: `python -m http.server 8000`
3. Open `http://localhost:8000` in your browser.

## Deploy free with Cloudflare Pages
1. Create a GitHub repository and upload `index.html` (and this README).
2. In Cloudflare Dashboard, go to Workers & Pages → Create → Pages → Connect to Git.
3. Select the repository.
4. Framework preset: None. Build command: leave blank. Build output directory: `/` (or `.` depending on the UI).
5. Deploy. Use the generated `https://....pages.dev` URL on Android/iPhone.
   Alternative: upload the folder through the Cloudflare Pages Direct Upload interface if available on your account.

## Important measurement limitations
- This is a prototype for approximate 2D image angles, not a validated ergonomic or medical measurement instrument.
- Correct side view, visible joints, stable camera, and good lighting matter.
- Current formulas are simple geometric estimates. The wrist angle is a rough proxy and may be unavailable if the hand is not detected.
- Pose landmarks cannot reliably infer all 3D rotations, wrist deviation, forearm twist, or exact anatomical reference angles from one ordinary camera view.
- Review results and validate against a trusted goniometer / trained observer before any formal study.
- Images and video are processed in the browser by this code; the AI models are downloaded from third-party CDNs on first use.
