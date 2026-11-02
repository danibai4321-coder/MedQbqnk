# MedQBank v1 — offline PWA

An original, standalone MCQ practice app. Includes six original demonstration questions. Not affiliated with UWorld or USMLE.

## Features
- Tutor mode with immediate explanation and timed mode with deferred review
- System filters; all/unused/incorrect/bookmarked question selection
- Bookmarks, local progress analytics, resume interrupted tests
- CSV import (including quoted commas/newlines), CSV template export
- JSON backup and restore between devices
- Service worker for offline operation after initial visit

## Run locally on Windows
1. Install Python 3 (or use another static web server).
2. Unzip the archive and open a terminal in the `medqbank` folder.
3. Run `python -m http.server 8000` (or `py -m http.server 8000`).
4. Open `http://localhost:8000` in Chrome or Edge.
5. Once loaded, it works offline in that browser, provided the service worker and cached files remain installed. You can install from the browser's Install app option.

Do not open `index.html` using `file://`: service workers cannot register from file URLs.

## Install on Android and Windows as a PWA
1. Host the files on an HTTPS static host (for example GitHub Pages or Netlify). HTTPS is required for PWA installation on devices other than localhost.
2. Open the HTTPS URL in Chrome on Android or Chrome/Edge on Windows.
3. Android: browser menu > Add to Home screen / Install app. Windows: browser address bar install icon or menu > Apps > Install this site as an app.
4. Open the app at least once while online, then test in airplane mode.

A local Windows server at `localhost` does not automatically make the site available on Android. Hosting via HTTPS is the simplest way to install on both devices. Once installed and cached, internet is not required for normal use.

## CSV columns
`id,system,subject,stem,optionA,optionB,optionC,optionD,answer,explanation`

`answer` is A/B/C/D or 0/1/2/3. Use unique IDs. Download a sample CSV template from the Import screen. Import only questions you own or are authorized to reproduce.

## PDF limitation
Automatic PDF parsing is **not** implemented in v1. PDFs have inconsistent answer formatting, diagrams, and multi-column layouts; conversion to structured CSV is the supported import path. Images embedded in questions are not yet supported.

## Data and privacy
All question data and progress are saved in browser localStorage, with a practical browser-dependent size limit (often around 5 MiB). Clearing site data can delete progress. Export JSON backups regularly. Devices do not sync automatically; transfer the JSON backup manually. The application makes no API calls and has no backend.

## Notes
This is a working MVP, not a production exam platform. It has no login, cloud sync, PDF parser, image support, or spaced repetition. Use current official NBME and USMLE resources to assess readiness.


## Version 2 additions
- Searchable question library with system and status filters
- Subject filtering when creating tests
- Per-question notes and confidence ratings (Again / Hard / Good / Easy)
- Learning insights: accuracy by system, study days, weak areas, activity
- Updated responsive navigation and design
- Keeps the same localStorage key as v1 to preserve progress when updating on the same origin. Export a backup first.

### Important limitations
- No automatic PDF parsing or image extraction; CSV import is supported.
- No cloud sync; use JSON export/import for transfers.
- Browser storage can be cleared; back up regularly.
- Only six original demo questions are bundled. Commercial question-bank content is not included.
- Test on the actual target browser/device before relying on it for exam preparation.
