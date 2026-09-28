# AI Master V11 Chat Update

This update keeps the existing Firebase login/chat and Meta AI connection and adds the requested chat features.

## Chat plus menu
- Camera
- Gallery/photo upload
- Video
- Document/file
- Audio/voice recording
- Location (browser GPS permission + Google Maps link)
- Contact (Firebase friends)
- Payment (UPI intent; real payment processing requires a payment provider)
- Event (event message stored in the chat)
- AI Images (opens the image picker for the current image workflow)

## Message states
- Typing indicator through Firebase Realtime Database
- Sent, delivered and read double ticks through Firestore
- Reply, copy, pin/unpin and delete
- Clear chat

## Friends
- Stable 6-digit Friend Code is created for each account and shown in Settings/Profile.
- Search a 6-digit code to open the user's public profile.
- Send and accept friend requests.
- Open a real Firebase chat after becoming friends.

## Status / Updates
- Text status
- Photo/video status upload
- 24-hour expiry
- Status viewer/read tracking
- Status replies

## Calls
- Existing Firebase Realtime Database + WebRTC audio/video calling is retained.

## Profile photo
- 512x512 JPEG crop
- Firebase Storage upload to a stable avatar path
- Cache-busting URL after save

## Meta AI on Vercel
The `api/meta-ai.js` and `api/health.js` routes make `/api/meta-ai` and `/api/health` available on Vercel. Set `META_MODEL_API_KEY` in Vercel Environment Variables. Optional `META_MODEL_API_URL` and `META_MODEL_NAME` can override the defaults.

## Firebase rules
Publish `firebase.rules.txt` and `storage.rules.txt` after deploying. These include `statuses`, `status replies`, `communities`, profile Friend Codes and status media.
