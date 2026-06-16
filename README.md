# Chism Cinematics — website

Immersive single-page site for **Chism Cinematics** (Joel Chism) — a wedding / commercial / music-video film studio in Boyds, MD.

**Live site:** _add your GitHub Pages URL here once it's published_

## What's in here
- `index.html` — the entire site (HTML + CSS + JS in one self-contained file).
- `videos/` — background hover clips + their poster images.
- `photos/` — image assets (e.g. the FX30 photo used in the Collab spec menu).
- `CLAUDE.md` — full project + brand context (so Claude Code picks up where we left off).

## View it locally
Double-click `index.html`, or run a tiny static server from this folder:

```bash
python3 -m http.server
```

then open http://localhost:8000

## Deploy with GitHub Pages
1. Push this folder to a GitHub repo.
2. Repo → **Settings → Pages → Source: Deploy from a branch**, Branch: `main`, folder `/ (root)`.
3. Live in ~1 minute at `https://<your-username>.github.io/<repo-name>/`.
4. _(Optional, later)_ Add `chismcine.com` as a custom domain in that same Pages screen, then point your domain's DNS at GitHub.

## Updating
Edit the files → commit → push. GitHub Pages rebuilds automatically.

## Still to do
- Add a **Web3Forms** access key (contact form) created with **joel@chismcine.com**.
- Real **Instagram** handle.
- Own short, muted, looping **clips** for Commercial / Music Videos / Short Films (drop into `videos/`).
- Self-host the About portrait (currently hot-linked from the old chismcine.com).
