# hoppoulegionfiles.org (local preview)

Small static ARG-style gate site. English only. Files live in this folder.

## Open locally

1. Serve this folder with any static file server (required so `config.js` loads and sessionStorage works across pages).
2. Open the printed URL in a browser (usually `http://127.0.0.1:<port>/` or `http://localhost:<port>/`).
3. Enter the password on the black gate page.

Example:

```bash
cd /workspace/hoppoulegionfiles
python3 -m http.server 8765
```

Then visit `http://127.0.0.1:8765/`.

## Password

- Default password: `northernstar` (exact match, lowercase, no spaces)
- Wrong password: subtle shake/fade; stays on the gate
- Correct password: unlocks the message and video page

## Change password, message, or video

Edit `config.js`:

```js
window.SITE_CONFIG = {
  password: "northernstar",
  youtubeId: "cwjmoTXkqUI",
  unlockKey: "hoppou_unlocked",
  message: "congratulations, you are now heading into something deeper.",
  messageColor: "#e34c3e"
};
```

- `password` — gate unlock string (case-sensitive)
- `youtubeId` — YouTube watch ID (from `https://www.youtube.com/watch?v=...`)
- `unlockKey` — sessionStorage key used after unlock
- `message` — centered text shown in the first viewport after unlock
- `messageColor` — message text color

## Pages

- `index.html` — black password gate
- `video.html` — black unlocked page with the centered message above the YouTube embed; redirects to gate if not unlocked
- `config.js` — password, message, message color, and YouTube ID

## Domain note

Title and this README refer to **hoppoulegionfiles.org** for ARG flavor only. No real DNS or hosting is required for local preview.

## Caveats

- Unlock uses `sessionStorage` (per browser tab/session). Closing the tab clears unlock.
- Opening `video.html` directly without unlocking redirects to the gate.
- Client-side password check is not secure; fine for ARG/preview, not for real secrets.
- YouTube embed needs network access in the browser.
