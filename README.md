# Sun & Moon OS (Cloudflare)

Deploy: `npx wrangler deploy`

## Live chat + calls
- Chat uses a Durable Object (`PairRoom`, binding `ROOM`) over a WebSocket. Nothing to set up.
- Voice/video calls are WebRTC (phone to phone). They work out of the box with Cloudflare's free STUN server.
- OPTIONAL but recommended: add a Cloudflare TURN key so calls also work on strict mobile networks.
  Dashboard > Realtime > TURN Server > Create. Then add two secrets to the Worker:
  `TURN_KEY_ID` and `TURN_KEY_API_TOKEN` (Settings > Variables and Secrets), or:
  `npx wrangler secret put TURN_KEY_ID` / `npx wrangler secret put TURN_KEY_API_TOKEN`

## GIFs (optional)
The GIF button only appears when a free Giphy key is set: create one at developers.giphy.com, then
`npx wrangler secret put GIPHY_API_KEY`. Without it everything else (stickers, photos, replies...) still works.

## Voice messages (Moonsta chat)
Tap the mic (it replaces Send while the message box is empty), talk, tap Send. Up to 60 seconds each, stored with the chat like photos.
The browser asks for microphone permission the first time. Needs HTTPS (Cloudflare gives you that). Nothing to configure.
