# WhatsApp Style React + Firebase Realtime v5

This build keeps the realtime chat/call architecture and fixes deployment-sensitive pieces.

## Fixed in v5

- Vite production build targets Node 22.
- Firebase Hosting rewrites `/api/meta-ai` and `/api/health` to Firebase 2nd-gen functions.
- Meta/Llama API endpoint updated to `https://api.llama.com/v1/chat/completions`.
- Meta/Llama response parsing supports both native and OpenAI-compatible response shapes.
- AI API key stays server-side in a Firebase secret.
- Realtime presence now uses connection nodes so multiple tabs/devices do not incorrectly mark each other offline.
- Firestore message update rules only permit read-receipt fields to change.
- Chat participant lists are immutable after creation.
- Settings now have functional local persistence for theme, notifications, storage/data, accessibility, language, privacy, and chat preferences.
- Production deployment uses Cloud Functions Node.js 22.
- JSX/JS source was parsed with TypeScript compiler checks in this environment.

## Important limitation of this environment

The build dependencies could not be downloaded because outbound npm registry DNS/network access is unavailable in the execution environment. Therefore `npm run build` was not executed here. The source was syntax-checked, JSON was validated, and the deployment configuration was audited. Run `npm install && npm run build` on a machine with npm network access before deployment.

## Production deployment

1. Install Node.js 22.
2. `npm install`
3. `npm run build`
4. `firebase login`
5. `firebase use meseage-60483`
6. `firebase functions:secrets:set META_MODEL_API_KEY`
7. `firebase deploy --only functions,hosting,firestore:rules,storage,database`

For Firebase Functions, the project may need the Blaze billing plan.

## Required for real calls

- HTTPS production URL (Firebase Hosting provides SSL).
- STUN is included.
- Configure a TURN provider for reliable calls through restrictive NAT/firewalls:
  - `VITE_TURN_URL`
  - `VITE_TURN_USERNAME`
  - `VITE_TURN_CREDENTIAL`

## Required Firebase console setup

- Authentication > Phone provider enabled.
- Production domains added to Authentication > Settings > Authorized domains.
- Cloud Firestore enabled.
- Storage enabled.
- Realtime Database enabled.
- Publish Firestore, Storage and RTDB rules.

## Meta/Llama

The in-app AI is a server-proxied Llama/Meta model API integration. It is not the same thing as the proprietary WhatsApp Meta AI service. The header link opens the official Meta AI website. The API key must never be placed in `VITE_*` frontend variables.
