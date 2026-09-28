# Production deployment checklist

## 1. Frontend build
- Node.js 22
- `npm install`
- `npm run build`

## 2. Firebase services
Enable Authentication > Phone, Firestore, Storage, and Realtime Database.
Deploy rules with `firebase deploy --only firestore:rules,storage,database`.

## 3. Meta/Llama AI
The browser never receives the AI API key. Firebase Hosting rewrites `/api/meta-ai` to the `metaAI` 2nd-gen function.

Set the secret:

`firebase functions:secrets:set META_MODEL_API_KEY`

Then deploy functions and hosting:

`firebase deploy --only functions,hosting`

The current default API endpoint is `https://api.llama.com/v1/chat/completions` and the default model is `Llama-4-Maverick-17B-128E-Instruct-FP8`.

## 4. WebRTC
For development, Google STUN is included. For reliable production calls across restrictive networks, configure a TURN service using:

- `VITE_TURN_URL`
- `VITE_TURN_USERNAME`
- `VITE_TURN_CREDENTIAL`

Do not commit TURN credentials to source control. Prefer deployment environment variables.

## 5. Phone auth
In Firebase Console:
- Enable Phone provider.
- Configure SMS region policy.
- Add every production domain to Authentication > Settings > Authorized domains.

## 6. Realtime Database
Create/enable Realtime Database and publish `database.rules.json`.
