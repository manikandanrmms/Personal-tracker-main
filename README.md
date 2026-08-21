# Command Center — Life OS

A single-file web app. No build step, no `npm install` — it's plain HTML that
loads React, Recharts, and the icon set from a CDN at runtime.

## Run it locally

Just double-click `index.html`, or serve it:

```bash
npx serve .
# or
python3 -m http.server 8000
```

Requires an internet connection (for the CDN scripts) the first time it loads
in a browser tab.

## Deploy it

Any static host works, since it's one file:

- **Netlify** — drag the folder onto app.netlify.com/drop
- **Vercel** — `vercel deploy` from this folder
- **GitHub Pages** — push to a repo, enable Pages on the `main` branch
- **Cloudflare Pages** — connect the repo or drag-and-drop upload

## Data & storage

Data is saved to the browser's `localStorage`, scoped to whatever domain you
open it from. That means:

- Data persists across reloads and browser restarts, on that device/browser only.
- It does **not** sync across devices or browsers — this is single-user, local-only storage.
- Clearing site data / browser storage will erase it. There's no export yet —
  ask Claude to add JSON export/import if you want a backup path.

## Notes for further development

- All state lives in one `data` object (`tasks`, `goals`, `habits`, `career`, `notes`) inside `index.html`.
- To swap local storage for a real backend later (e.g. Supabase, Firebase), only the `storage.get` / `storage.set` functions near the top of the script need to change — the rest of the app is storage-agnostic.
- Tailwind is loaded via the CDN JIT script, so any Tailwind utility class works without a config file.
