# Netlify deployment — v7

This project is a Vite/React source project. If Netlify is connected to Git, push/replace the source files from this archive before redeploying.

## Build settings
- Build command: `npm run build`
- Publish directory: `dist`
- Node: 22

`netlify.toml` already contains these settings and the React SPA fallback.

## Important: old rtdb build error
The old build error said:

`"rtdb" is not exported by "src/realtime.js"`

The v7 source deliberately does **not** import `rtdb` from `src/realtime.js`. The UI imports the Firebase Realtime Database instance directly from `src/firebase.js` and `src/realtime.js` keeps its RTDB handle private. This removes the stale named-export dependency that caused the Rollup failure.

If Netlify still prints the exact old error after deploying v7, Netlify is building an older repository/branch/commit rather than these source files. Check the deployed commit and repository/branch in Netlify.

## Netlify Functions
The Meta AI proxy is in `netlify/functions/meta-ai.mjs`. Set `META_MODEL_API_KEY` in Netlify's environment variables if AI is enabled.
