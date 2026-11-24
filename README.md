# First Line

Free, offline-first screenplay reader and film production workspace for iPhone and iPad (PWA).
No account, no subscription, no paid API. All data stays on the device (IndexedDB).

## Structure
- `index.html`: app shell
- `css/app.css`: dark cinematic UI
- `js/app.js`: storage, tabs, production tools (breakdown, director, shots, takes, schedule), backup/restore, CSV
- `js/reader.js`: PDF reader (pdf.js), scene detection, highlights and notes
- `js/export.js`: production report PDF (pdf-lib)
- `vendor/`: pdf.js (Apache-2.0) and pdf-lib (MIT), bundled so the app works offline
- `sw.js`, `manifest.webmanifest`, `icons/`: PWA files (icons and iOS splash screens)
- `samples/`: test screenplays (PDF, FDX, Fountain, TXT)

## Deploy over HTTPS (pick one, all free)
**GitHub Pages:** create a repo, upload the *contents* of this folder to the root, then Settings > Pages > Deploy from branch > `main` / root. Your URL will be `https://<user>.github.io/<repo>/`.
**Netlify:** go to app.netlify.com/drop and drag this folder in.
**Cloudflare Pages:** create a project > Direct Upload > upload the folder.

## Install on iPhone
1. Open the HTTPS URL in **Safari** (not an in-app browser).
2. Wait for the page to finish loading once (this caches the app for offline use).
3. Tap Share > **Add to Home Screen** > Add.
4. Launch from the Home Screen. It now works in airplane mode.

## Using the reader
Script tab > choose a PDF > Import. Scene headings are detected per page. Turn on **Highlight** and drag over text, or **Note** and tap a spot. Tap a mark to edit or delete it. Notes are linked to their page and the scene it belongs to. Swipe left/right to turn pages; **Full screen** gives a larger page.

## Backups (important)
iOS can clear website data for apps that go unused. The app asks Safari for persistent storage, but keep backups: Export tab > **Export JSON backup** (includes the PDF and annotations) and save it to Files or iCloud. Restore with **Restore backup**.

## Updating the app
Change files, then bump the `CACHE` name in `sw.js` (e.g. `first-line-v2`) so installed copies refresh.

## Known limits
- PDF report export uses Latin-only PDF fonts; Arabic text appears as `?` there. Use JSON or CSV for non-Latin data.
- FDX/Fountain/TXT are shown as formatted text without highlight/notes (PDF has full annotation).
