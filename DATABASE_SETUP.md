# Firebase Realtime Database setup

This version uses **Cloud Firestore** for chats/messages and **Realtime Database** for presence, typing indicators and WebRTC call signaling.

1. Open Firebase Console for project `meseage-60483`.
2. Build → Realtime Database → Create database.
3. Choose a location and create it.
4. In Realtime Database → Rules, paste `database.rules.json` and publish.
5. If Firebase gives you a database URL, put it in `.env` as `VITE_FIREBASE_DATABASE_URL` and restart Vite. The app uses the default database when the URL is blank.
6. Firestore → Rules: publish `firebase.rules.txt`.
7. Storage → Rules: publish `storage.rules.txt`.

## Two-user test

Open the app in two browsers/profiles and sign in with two different phone numbers. Copy the second account's Firebase UID from Firebase Authentication → Users. On the first account tap **New chat (✎)** and enter that UID.

Messages, read receipts and typing status are then synchronized through Firebase.

## Calls

Open the chat and tap ☎ for voice or ▣ for video. The call media uses WebRTC directly between browsers; Firebase Realtime Database is used for signaling (offer/answer/ICE) and incoming-call state.

A public STUN server is included for basic connectivity. For production reliability across restrictive NAT/firewalls, configure a TURN server using `VITE_TURN_URL`, `VITE_TURN_USERNAME` and `VITE_TURN_CREDENTIAL`.
