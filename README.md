# Sun & Moon OS (Cloudflare)

Deploy: `npx wrangler deploy`

## Live chat + calls
- Chat uses a Durable Object (`PairRoom`, binding `ROOM`) over a WebSocket. Nothing to set up.
- Voice/video calls are WebRTC (phone to phone). They work out of the box with Cloudflare's free STUN server.
- OPTIONAL but recommended: add a Cloudflare TURN key so calls also work on strict mobile networks.
  Dashboard > Realtime > TURN Server > Create. Then add two secrets to the Worker:
  `TURN_KEY_ID` and `TURN_KEY_API_TOKEN` (Settings > Variables and Secrets), or:
  `npx wrangler secret put TURN_KEY_ID` / `npx wrangler secret put TURN_KEY_API_TOKEN`
