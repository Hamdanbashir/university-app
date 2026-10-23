# Air University — Classroom Command Center

A responsive, client-side timetable viewer for the Fall 2026 university schedules. The app is built from local HTML, CSS, JavaScript, a supplied Air University logo, and bundled timetable/teacher data. No framework, build step, login, API key, or paid service is required.

## Run it

- **GitHub Pages:** Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save. Then visit the Pages URL after deployment completes.
- **Locally:** Download the full repository ZIP, extract **all files**, and open `index.html` in Chrome or Edge. Do not open an isolated `index.html` without the `data/` and `assets/` folders.
- **Development:** `python -m http.server 8000` from this directory, then visit `http://localhost:8000`.

## Files

- `index.html` — dashboard structure and navigation.
- `styles.css` — responsive navy university dashboard styling.
- `app.js` — schedule engine, live clock, room and teacher views, analytics, local admin edits, import/export.
- `assets/air-university-logo.svg` — the user-supplied Air University image embedded in an SVG wrapper.
- `data/timetable.js` and `data/teachers.js` — self-contained data loaded by the browser, including when opened as a local file.
- `data/timetable.json` and `data/teachers.json` — editable, structured copies of the same data.

## How the clock and statuses work

The clock uses the IANA `Asia/Karachi` timezone. Every second it updates the time, and at each new minute it recomputes the selected floor's scheduled room status using the current Pakistan weekday and time. Classes are **In class** from their start time (inclusive) to end time (exclusive); **Upcoming** when the next class begins within 80 minutes; otherwise **Available**. The weekday selector allows browsing other days; live mode follows Pakistan time.

**These are scheduled states, not verified real-world occupancy.** There is no connection to university attendance systems, IoT room sensors, or a live scheduling backend. The timetable changes only if a user edits/imports data locally or the source files in the repository are updated.

## Data and limitations

The packaged data contains 1,082 distinct extracted records across 29 room identifiers. Sources: 56-page classwise final timetable, 56-page AUSOM morning final timetable, and BS English/BSCMS Fall 2026 timetable; the teachers directory is also enriched from `teachers_and_subjects.csv`. Some entries may contain extraction errors, naming inconsistencies, duplicated classes from different sources, or unresolved conflicts. The Analytics page highlights room overlaps that need manual review. The source PDFs are **not** packaged here, but the extracted data is included.

- All **nine AUSOM floor selectors** are available, but floor-plan geometry is schematic and only timetable-identified rooms are shown.
- Teachers are aggregated by their written names; spelling variants may appear as separate people.
- Admin changes persist in the current browser using `localStorage`; they are **not** synced across browsers/devices or pushed to GitHub.
- The application is a functional standalone **prototype**; production university use would require a secured backend, verified timetables, role-based authentication, server-side edits, and official floor plans.

## Tests performed

Browser automation checked: initial dashboard, nine AUSOM floors, room counts, faculty directory, schedule view, analytics, admin form, simulated Monday 08:30 PKT with scheduled room statuses, and console errors. The code was also checked with `node --check`.

## AUSOM first-floor map

The supplied AUSOM 1st-floor plan is included in `assets/ausom-floor-1.svg` (a self-contained wrapper around the compressed image). Select AUSOM → 1st Floor to view it. Classroom **A001** is selectable and updates with the timetable when records exist; without an assigned timetable it shows **No timetable data**, not an invented availability status. Markers identify the auditorium, conference room, offices, information desk, entrance, lifts, stairs, and washrooms. Other floors retain the schematic room-grid view until their plans are provided.