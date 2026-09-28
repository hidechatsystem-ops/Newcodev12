# AI Master v9 – Friends + WhatsApp-style chat upgrade

This package keeps the existing Firebase login/chat system and the existing Netlify Meta AI proxy.

## Included
- Friends: find users by name, send request, accept/decline, friends list, open chat.
- Existing Firebase phone login remains unchanged.
- Existing Meta AI `/api/meta-ai` Netlify function remains unchanged.
- Meta AI in-app voice conversation: microphone speech recognition + spoken replies using browser TTS.
- Friend voice and video calls using the existing Firebase Realtime Database WebRTC call system.
- Chat + menu: photo, video, document, audio and voice messages.
- Message actions: pin/unpin and delete your own message.
- Chat menu: clear chat.
- Profile photo crop/save uses a new Storage filename and compressed 512x512 JPEG to avoid stale cached avatars and long uploads.
- Public profile search index now stores `nameLower`.

## Deploy on Netlify
1. Upload this project to GitHub and connect the repository to Netlify, or upload the project through your normal Netlify workflow.
2. Build command: `npm run build`
3. Publish directory: `dist`
4. Node: 22 (already set in `netlify.toml`).
5. Keep the existing Netlify environment variable `META_MODEL_API_KEY` and any existing `META_MODEL_API_URL` / `META_MODEL_NAME` values. Do not put the secret in the frontend.
6. Deploy.

## Firebase rules
Publish the included:
- `firebase.rules.txt` to Firestore Rules.
- `storage.rules.txt` to Storage Rules.

The rules allow authenticated chat members to read/write chat messages, including pinning and clearing, and allow authenticated users to read chat attachments while only the uploading user can write to their upload path.

## Browser permissions
Voice messages and voice/video calls require microphone/camera permission. Meta AI voice call uses browser SpeechRecognition and SpeechSynthesis; Chrome on Android is recommended.

## Important
"Meta AI voice call" here means an in-app voice conversation with the Meta model endpoint already configured in your Netlify function. It is not a phone/PSTN call to Meta.
