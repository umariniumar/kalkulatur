# Kalkulatur (Kalkulator eFaktur)

Static MVP for calculating DPP, PPN, PPh23, and net transaction value from selling price.

## Files
- `index.html` — application
- `manifest.webmanifest` — installable web app metadata
- `sw.js` — offline cache/service worker
- `favicon.svg` — app icon

## Deploy
Use GitHub + Vercel. Put all files in the repository root.

## Notes
- The calculation formulas intentionally follow the workbook specification supplied for this project.
- The app stores the current workspace locally in the browser; no account/database is required for MVP.
