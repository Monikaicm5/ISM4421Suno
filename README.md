# Suno Studio

A single-page AI music generator built on the [Suno API](https://docs.sunoapi.org).
Each user pastes their own Suno API key — nothing secret lives in the code.

## Features
- **Email login** (Supabase Auth) – sign up, sign in, forgot/reset password, sign out. The app is only usable when signed in.
- **API key box** – stored only in the user's browser (optional), with live credit balance
- **Simple mode** – describe a song, Suno writes lyrics and music
- **Custom mode** – title, your own lyrics, style, excluded styles, vocal gender, duration, style/weirdness/variety controls
- **AI lyrics helper** – generate lyrics from a short idea and drop them into the editor
- **Instrumental toggle** and model picker (V6, V6 Wild, V6 Mini)
- **Results** – live status, 2 variations per request, cover art, in-page player, MP3 download, lyrics view
- **History** saved in the browser; unfinished jobs resume polling after a reload

## Deploy to Netlify
Drag-and-drop this folder into Netlify, or connect the repo. No build command is needed —
`netlify.toml` publishes the root folder and adds a simple rewrite (`/suno-api/*` → `https://api.sunoapi.org/*`)
so browsers don't run into CORS. No serverless functions are involved.

## Supabase setup (one time)
The app uses the Supabase project `oyffhrvjiyzkmkoahkvx`; its public URL and publishable key are in `index.html`
(both are safe to ship in a browser). In the Supabase dashboard go to **Authentication → URL Configuration** and:
1. Set **Site URL** to your Netlify URL (e.g. `https://your-site.netlify.app`).
2. Add the same URL to **Redirect URLs**.

Without this, confirmation and password-reset emails send people to `localhost`.

## Run locally
Open `index.html` directly, or serve the folder (`npx serve .`). Off Netlify, the app calls
`https://api.sunoapi.org` directly.

Get an API key at https://sunoapi.org/api-key.
