# Air University Classroom Management Dashboard

Open **index.html** in a browser to use the standalone demo, or publish the repository with GitHub Pages (Settings → Pages → Deploy from a branch → main → /root).

## Data

- `data/timetable.json`: 683 extracted timetable entries across 26 room identifiers and 66 sections.
- The HTML also embeds these timetable entries so it can work without a server.
- The Teachers and Subjects pages include the previously imported teacher directory plus names from the timetable.
- AUSOM shows all nine floor selectors; rooms are shown only on floors with extracted records.

## What is live?

The clock uses **Asia/Karachi** timezone. Scheduled room status is recalculated based on the current Pakistan time and weekday. It does **not** connect to a university scheduling API, verify teacher attendance, or confirm physical room occupancy. The app is a local timetable viewer, not a real-time university backend.

## Known limitations

- Some extracted PDF entries may require manual verification, and the AUSOM Morning timetable has not been fully reconciled.
- Room layout is schematic, not an official floor plan.
- Admin edits are not stored in a database or synchronized between devices.
- University branding uses a stylized monogram, not a verified official logo.
