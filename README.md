# Poker Live

A multiplayer Texas Hold'em showdown website using Express + Socket.IO. Each player joins the same room from their own phone, selects an available seat, privately enters two hole cards, and chooses HOLD or FOLD. The host enters five community cards and presses SHOW to reveal and evaluate active players. Folded players cannot win.

## Run locally

```sh
npm install
npm start
```

Open http://localhost:3000. For phone testing, use the computer's LAN IP and port 3000, with both devices on the same network.

## Host publicly

Upload the repository to GitHub and deploy as a **Web Service** on Render (https://render.com). Build command: `npm install`. Start command: `npm start`. Render will provide a public `https://...onrender.com` URL. Node.js hosting with WebSocket support is required; static hosting such as Netlify Drop will **not** synchronize players.

## Notes

- The host's SHOW button only works with five community cards and two cards for each HOLD player.
- Card data is sent to the server; opponents receive card backs until SHOW.
- Rooms are in memory: a server restart erases rooms. A disconnected player is removed before SHOW. For production, add authentication, reconnect tokens, persistent state, rate limiting and a shared store for multi-instance deployment.
- All players can see the community board while the hand is being prepared.
- This release calculates final winners, **not** pre-show probabilities.
