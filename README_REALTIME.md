# Realtime v4

This build uses:
- Cloud Firestore: chats, messages, read receipts, public profiles, chat list.
- Realtime Database: online/offline presence, typing indicator, WebRTC signaling and incoming-call state.
- WebRTC: browser microphone/camera media path.

## Firebase
1. Enable Authentication > Phone.
2. Create Firestore database and publish `firebase.rules.txt`.
3. Create Storage and publish `storage.rules.txt`.
4. Create Realtime Database and publish `database.rules.json`.
5. Add the Realtime Database URL to `.env` as `VITE_FIREBASE_DATABASE_URL` if your database URL differs from the default.

## Test two users
Sign in with two different phone numbers in two browser profiles. Copy the second user's Firebase Auth UID. In New chat, enter that UID. Messages sync in real time.

## Presence and typing
Presence uses Realtime Database `onDisconnect` and connection state. Typing writes to `typing/{chatId}/{uid}` and is removed after the user stops typing.

## Calls
Voice/video calls use WebRTC. Firebase Realtime Database carries offer/answer/ICE signaling. The included STUN server is for basic testing. For production reliability across restrictive NAT/firewalls, configure a TURN server with `VITE_TURN_URL`, `VITE_TURN_USERNAME`, and `VITE_TURN_CREDENTIAL`.

Browsers require HTTPS (or localhost) for camera/microphone access.
