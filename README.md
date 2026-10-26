# Raja Mantri Chor Sipahi — online rooms

A small mobile-friendly real-time multiplayer game. Supports 4–12 players per room, private roles, a Mantri guess, host-controlled role reveal, and a leaderboard.

## Easiest way to publish (Render + GitHub)

This project needs a Node.js server; it cannot be hosted as a plain static HTML page because rooms and private roles need a live server.

1. Download and unzip `raja_mantri_chor_sipahi.zip`.
2. Create/sign in to GitHub and make a **new public repository**.
3. Upload the contents of this folder to the repository root. Make sure `package.json`, `server.js`, and `public/index.html` are at the top-level / correct folders.
4. Sign in to Render and choose **New → Web Service**. Connect the GitHub repository.
5. Use these settings:
   - Runtime: **Node**
   - Build command: `npm install`
   - Start command: `npm start`
   - Instance type: Free (if available for your account/region)
6. Click **Deploy**. Wait for Render to finish and open the `https://...onrender.com` URL it gives you.
7. Create a room in the game. Tap **Copy invite link** and send that URL to your friends. Everyone opens the same link on their phone and enters a nickname.

## Rules in this build

- 4–12 connected players.
- One Raja, one Mantri, one Chor, one Sipahi. Any additional players become Praja.
- Only each player receives their own role privately. The role list is revealed to everyone only after the host taps **Reveal roles**.
- The Mantri can make one guess per round.
- Scores: Raja +1000; Mantri +800 for a correct guess, −400 for an incorrect guess (score cannot go below zero); Sipahi +500; Chor +400 if the Mantri guesses incorrectly; Praja +200.
- The room host can start a round and reveal roles. Host status moves to another player if the host disconnects.
- Rooms are in server memory and are temporary. If the server restarts or sleeps, rooms and scores reset. Don't use the game for sensitive information.

## Local test

Install Node.js 18 or newer. In this folder run:

```bash
npm install
npm start
```

Then open `http://localhost:3000` in your browser. For testing multiple players on one computer, use multiple browser profiles or devices on the same reachable server.

## Notes

This is a lightweight friends game, not a hardened production service. The game uses a simple room code and nickname, without accounts. A player reconnecting after a disconnect may need to rejoin the room. The live host URL must be shared; the HTML file alone is not a public multiplayer link.
