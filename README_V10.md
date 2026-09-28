# AI Master V10 update

- Existing Firebase login, profile, friends and calling are preserved.
- Chat composer now has Camera, Gallery, Video, Document, Audio, Location and Contact actions.
- Voice-message recording uses the browser microphone and uploads to Firebase Storage.
- Messages support reply, copy, pin/unpin, delete, clear chat, typing state, delivered ticks and read/seen ticks.
- Settings main list uses larger labels with no descriptive text.
- Profile photo crop/save keeps compressed 512px JPEG uploads with unique filenames.
- Meta AI keeps the `/api/meta-ai` Netlify endpoint.

## Netlify AI key
Set one of these server-side Netlify environment variables (do not put the secret in frontend code):
`META_MODEL_API_KEY` (recommended), `META_AI_API_KEY`, `META_API_KEY`, or `LLAMA_API_KEY`.
Optional: `META_MODEL_API_URL` and `META_MODEL_NAME`.
After changing environment variables, redeploy the site.
