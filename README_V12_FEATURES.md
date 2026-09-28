# AI Master V12

V12 keeps the existing Firebase chat/login structure and adds a safer build-cleanup pass plus richer WhatsApp-style status behavior.

## Included
- Firebase realtime chat, typing, delivered/read ticks
- Media, location, contact, payment and event message types
- Friend code, friend requests and friend chat
- Audio/video call entry points for friends
- Status photo/video/text publishing
- 24-hour status expiry
- Status view counter (`views`)
- Status like counter (`likes`)
- Status reply
- Own-status delete
- Profile photo crop and compressed upload
- Meta AI route preserved at `/api/meta-ai`

## Deploy
1. Keep your existing Vercel project connected to the same repository.
2. Upload/commit the project files.
3. Keep `META_MODEL_API_KEY` (and optional `META_MODEL_API_URL`, `META_MODEL_NAME`) in Vercel Environment Variables.
4. Deploy.
5. Publish the updated `firebase.rules.txt` to Firestore Rules so status likes are allowed.
