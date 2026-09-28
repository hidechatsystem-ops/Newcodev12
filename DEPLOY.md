# Firebase Hosting deployment

1. Install Firebase CLI:

```bash
npm install -g firebase-tools
```

2. Login:

```bash
firebase login
```

3. Build the React app:

```bash
npm run build
```

4. Deploy Hosting + Firestore rules + Storage rules:

```bash
firebase deploy --only hosting,firestore:rules,storage
```

After deployment, copy the Firebase Hosting domain into Firebase Console → Authentication → Settings → Authorized domains.

For Meta AI, keep the `/api/meta-ai` Node server on a backend host (Cloud Run, Cloud Functions, Render, Railway, etc.) and configure your frontend production proxy/reverse-proxy to route `/api/*` to that server. Do not put `META_MODEL_API_KEY` in frontend environment variables.


## v5 production deploy

Use Node.js 22. Run `npm install`, then `npm run build`. Deploy with `firebase deploy --only functions,hosting,firestore:rules,storage,database`. Before deploying functions, set `META_MODEL_API_KEY` with `firebase functions:secrets:set META_MODEL_API_KEY`.
