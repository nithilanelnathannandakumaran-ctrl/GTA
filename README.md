# GTA E on Cloudflare

The game is one static file (`public/index.html`), so there is no server code to run.

## Option A: Cloudflare Pages, no tools (easiest)
1. Cloudflare dashboard > Workers & Pages > Create > Pages > Upload assets.
2. Name the project (for example `gta-e`) and upload the **public** folder (or the zip).
3. Click Deploy. You get `https://gta-e.pages.dev`.
   To update later: Create deployment and upload the folder again.

## Option B: Wrangler (command line)
    cd gta-e
    npx wrangler login
    npx wrangler deploy

This publishes `public/` as a Workers static-assets site at `https://gta-e.<your-subdomain>.workers.dev`.

## Option C: Git
Push this folder to GitHub/GitLab, then Workers & Pages > Create > Pages > Connect to Git.
Build command: leave empty. Build output directory: `public`.

## Notes
- If you turn on **Rocket Loader** in Speed > Optimization, leave it alone: the scripts are marked `data-cfasync="false"` so it will not reorder them.
- Three.js loads from cdnjs and fonts from Google Fonts, so players need internet access.
- Saves (character look, graphics choice, best scores) use the browser's localStorage, so they are per device and per domain.
