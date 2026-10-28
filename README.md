# Morrow – mortgage planning PWA (England)

Static, no build step, no backend. All paths are relative, so it works at `https://<user>.github.io/<repo>/` without base-path config.

## Deploy to GitHub Pages
1. Create a GitHub repository and upload every file in this folder to the `main` branch (keep `.github/workflows/deploy.yml`).
2. Settings → Pages → Build and deployment → Source: **GitHub Actions**.
3. The workflow runs on each push to `main`. The URL appears in Settings → Pages and in the Actions run.
(No Actions? Choose "Deploy from a branch", `main`, `/ (root)`.)

## Local development
`python3 -m http.server 8000` in this folder, then open http://localhost:8000 (service workers need localhost or HTTPS).

## Updating and rollback
Bump `V` in `sw.js` (e.g. `morrow-v2`) with each release so devices refresh their cache. Pages is network-first, so online users get updates on the next load. Roll back by reverting the commit on `main` and letting the workflow redeploy.

## Troubleshooting
- 404 after deploy: check Pages source is set and the workflow succeeded.
- Old version showing: hard refresh, or bump the cache name.
- No install prompt: needs HTTPS; on iPhone use Share → Add to Home Screen.

## Privacy
Data stays in browser local storage on the device. No accounts, analytics, trackers or third-party scripts or fonts. Not encrypted; lost if browser data is cleared. Use My data to export a copy.

## Method and limits
Monthly interest on the opening balance, standard amortisation formula; lenders often use daily interest, so figures are estimates. Lump sums are applied at the start. Property value is held constant unless you set a what-if. Not financial advice.
Not yet included: rate changes mid-term, part-and-part mortgages, payment dates, push notifications, accounts or cloud sync, commercial placements (none are built; keep any future ones behind a flag and get FCA and legal advice first), automated test suite.

## Hosting alternatives
Cloudflare Pages, Netlify and Vercel can serve the same files unchanged. Check each provider's current free-plan limits and commercial-use terms before relying on them.
