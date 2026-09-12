# Cozy Vinyl Player 🎼☕️

A browser-based "vinyl player" for your Spotify account. Your playlists show up as records in a crate — pick one, and the needle drops.

No backend, no build step — a single HTML file talking directly to Spotify's own APIs.

## How it works

- **Auth:** Spotify OAuth 2.0 (Authorization Code + PKCE), entirely client-side.
- **Data:** Spotify Web API (`/me/playlists`) to load your library.
- **Playback:** Spotify Web Playback SDK — turns the browser tab into a Spotify Connect device. Requires a **Spotify Premium** account.

## Setup

1. Create a free app at the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard).
2. Add your hosting URL as a **Redirect URI** in that app's settings (must match exactly, including path).
3. Check **Web API** and **Web Playback SDK** under "Which API/SDKs are you planning to use?"
4. Open the hosted page, paste in your **Client ID**, and click **Connect Spotify**.

## Running locally

```bash
python3 -m http.server 8080
```

Then visit `http://127.0.0.1:8080/vinyl-spotify.html` (this exact URL must also be added as a Redirect URI in your Spotify app).

## Hosting on GitHub Pages

Enable Pages under repo **Settings → Pages** (deploy from the `main` branch, root folder). Add the resulting `https://<username>.github.io/<repo>/vinyl-spotify.html` URL as another Redirect URI in your Spotify app.

## Notes

- Your Client ID is typed into the page at runtime and kept only in `sessionStorage` — it's never hardcoded into the file, so this repo is safe to keep public.
- Streaming requires Spotify **Premium** — free accounts can log in and browse playlists, but Spotify blocks the Web Playback SDK from streaming audio for them.
