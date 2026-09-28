# AI Master — Friends + Profile Photo Fix

## What was added
- Settings → Friends
- Search signed-in users by name
- User profile/avatar display
- Real Firebase friend requests
- Accept / Decline requests
- Real Firebase friendships
- Chat button for accepted friends
- Profile photo crop/save uses a compressed 512×512 JPEG
- Every avatar upload gets a fresh filename to avoid browser cache problems
- Existing Firebase Phone Login, chats, calls and Meta AI remain in place

## Firebase rules
The file `firebase.rules.txt` contains the required Firestore rules for `friendRequests` and `friendships`.

If you use Firebase CLI:
```bash
firebase deploy --only firestore:rules
```

Or copy the contents of `firebase.rules.txt` into Firebase Console → Firestore Database → Rules and publish.

The existing Storage rules already allow the signed-in user to write under:
`users/{uid}/...`

## Netlify
Deploy this project normally:
```bash
npm install
npm run build
```
Then publish the `dist` folder through your existing Netlify Git connection.

No new API key is needed for Friends.

## Important
The Friends feature uses the same Firebase project already present in this project. Do not replace the Firebase project configuration.
