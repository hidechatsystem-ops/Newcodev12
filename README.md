# WhatsApp-style React + Firebase — upgraded build

This build uses the supplied Firebase project configuration for `meseage-60483` and includes:

- Firebase Phone OTP login + reCAPTCHA
- Firestore profile sync
- Firebase Storage profile photo upload
- Profile photo crop + zoom before saving
- WebAuthn platform biometric/device unlock
- Chats / Updates / Communities / Calls navigation
- Settings and profile screens
- Meta AI chat screen with official Meta Model API server proxy
- Local chat history for the Meta AI screen
- Firebase rules starters

## Install

```bash
npm install
```

## Start React

```bash
npm run dev
```

## Start Meta AI server

Create `.env` from `.env.example`, add your Meta Model API key, then:

```bash
npm run server
```

The server uses the current Meta Model API Chat Completions endpoint and `muse-spark-1.3` by default. The key stays on the server.

## Important phone-auth note

Firebase's current web phone-auth docs require reCAPTCHA, an enabled Phone provider, an SMS region policy, and an authorized domain. The docs also state localhost is not an authorized hosted domain for phone authentication. Use Firebase fictional test phone numbers during local development, or deploy to an authorized HTTPS domain.

## Biometric note

WebAuthn can invoke a platform authenticator such as fingerprint, face unlock, or the device's secure credential on compatible browsers. For production-grade account recovery, server-side WebAuthn challenge verification should be added; this build uses a local credential identifier for the app-lock demo.

## v4 real-time features
- Firestore real-time 1:1 messages
- Read receipts (✓✓)
- Realtime typing indicator
- Realtime online/offline presence
- WebRTC voice/video calls with Firebase RTDB signaling
- Incoming call UI, accept/decline, mute, camera toggle, hang up
- Optional TURN server configuration

See `DATABASE_SETUP.md` before testing realtime features.


## Login v8
Every login request generates a fresh random 6-digit demo verification code. The code is displayed on the verification screen. Real SMS is not sent in demo mode.


## Netlify build fix
The Firebase Auth `signInAnonymously` method is imported and exported from `src/firebase.js`, matching the import used by `src/main.jsx`.

The login demo generates a fresh 6-digit code for each request.
