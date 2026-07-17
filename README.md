# The Rating Table

A seven-dimension board game rating method, built as an installable web app (PWA) for a YouTube board game channel.

- **Sliders 1–5** on each dimension (3 = a genuinely average game)
- **One overall score out of 10**, where **5 is dead average**
- **Adjustable weights** so the overall reflects what you care about
- **Collection** with sort, edit, delete — saved in the browser
- **Box art** per game (auto-downscaled), with a tidy monogram placeholder when none is set
- **Scorecard PNG export in three formats** — Wide 1280×720 (video), Square 1080×1080 (feed posts), Vertical 1080×1920 (Shorts / community posts)
- **Copy summary** text for video descriptions
- Works **offline** and **installs to your phone/desktop**

## The seven dimensions
Fun & Enjoyment · Depth & Strategy · Replayability · Player Interaction · Accessibility · Theme & Immersion · Components & Production

## Files
```
index.html              the whole app
manifest.webmanifest    PWA manifest (name, icons, colors)
sw.js                   service worker (offline + install)
icons/                  app icons (192, 512, maskable, apple-touch, favicon)
README.md               this file
```

## Deploy to GitHub Pages

1. Create a new repo (e.g. `rating-table`) and upload every file **keeping the `icons/` folder intact**.
   - Via the web: **Add file → Upload files**, drag the whole folder in, commit.
   - Via git:
     ```bash
     git init
     git add .
     git commit -m "Rating Table app"
     git branch -M main
     git remote add origin https://github.com/<you>/rating-table.git
     git push -u origin main
     ```
2. In the repo: **Settings → Pages**. Under **Build and deployment**, set **Source: Deploy from a branch**, **Branch: `main` / `/ (root)`**, save.
3. Wait ~1 minute. Your app is live at `https://<you>.github.io/rating-table/`.

> A service worker requires **HTTPS**, which GitHub Pages provides automatically. It will **not** install or cache if you open `index.html` directly with a `file://` path.

## Install it
- **iPhone (Safari):** open the Pages URL → Share → **Add to Home Screen**.
- **Android/Chrome & desktop:** open the URL → tap **Install App** in the header (or the browser's install icon).

## Updating the app later
When you change `index.html` or icons, bump the cache version in `sw.js` (e.g. `rating-table-v2` → `v3`) so devices pull the new version instead of serving the old cached one.

## App icon
The app icon is **embedded directly in `manifest.webmanifest` and `index.html`** as data URIs, so it shows even if the `icons/` folder is missing. The `icons/` files are still included for the favicon and older browsers.

If you ever see a generic gray icon on install, it means the manifest wasn't read. Check that:
- You installed from the **live GitHub Pages URL** (`https://<you>.github.io/rating-table/`), not a local `file://` path or a preview.
- `index.html`, `manifest.webmanifest`, and `sw.js` all sit in the **repo root** (not inside a subfolder). If you dragged a folder into GitHub's uploader, open the repo and confirm the files aren't nested under an extra `rating-table/` directory.

## Data & privacy
Everything is stored locally in your browser (`localStorage`), including box art (downscaled to keep it small). Nothing is uploaded anywhere. Clearing site data or the browser cache erases your collection, so export scorecards for anything you want to keep.

## Fonts
Loads **Fraunces** and **Hanken Grotesk** from Google Fonts. Online the first time; cached for offline use afterward.
