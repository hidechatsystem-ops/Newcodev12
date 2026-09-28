# Firebase setup for v5

Project: `meseage-60483`

Enable:
- Authentication > Phone
- Cloud Firestore
- Cloud Storage
- Realtime Database

Deploy rules:

```bash
firebase deploy --only firestore:rules,storage,database
```

For production AI, set the secret:

```bash
firebase functions:secrets:set META_MODEL_API_KEY
```

Then deploy:

```bash
npm install
npm run build
firebase deploy --only functions,hosting,firestore:rules,storage,database
```

Add your production website domain under Authentication > Settings > Authorized domains so Phone Auth can complete.
