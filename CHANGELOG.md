# Changelog

All notable changes to Coffee Brewing Control are documented here.

The project was developed iteratively before its first public GitHub release. Earlier entries are intentionally condensed to major user-facing and architectural milestones rather than every intermediate test or debugging change.

## [4.3.5] - 2026-09-17

### Changed
- Renamed user-facing terminology from **Coffee Brew Control** to **Coffee Brewing Control**.
- Renamed the chart title from **Brew Control Chart** to **Brewing Control Chart**.
- Refined chart zoning into semantic **Strong / Weak** and **Under / Over** overlay bands; corner regions inherit both meanings.
- Kept the target area in muted sage and brew-ratio lines in smoky plum to further distinguish the visual design from published SCA chart artwork.
- Corrected automatic beverage-mass estimation and Brew Ratio guide lines to use the full mass-balance relationship, and updated the Classic Filter liquid-retention default from 2.0 to 2.1.
- Corrected the visible HTML document version.

### Added
- In-app **About & References** dialog.
- In-app **Changelog** dialog.
- Visible app version information in Settings.
- Public-facing explanation of the tool's educational / repeated-test purpose, configurable ranges, beverage-mass estimation, local storage, references, and non-affiliation with SCA.

### Compatibility
- Existing browser data continues to use the legacy storage key `coffeeBrewControlClassroomV2`.
- Existing backup files remain importable because the legacy backup format identifier `coffee-brew-control-backup` is retained.

## [4.3.4.1]

### Added
- Current class, practice session, and selected-record count in the Class chart filter context.
- Reversible roster exclusion with an excluded-student list and restore action.

### Preserved
- Historical records and instructor feedback remain linked to the same student ID when a student is excluded and later restored.

## [4.3.4]

### Added
- Reusable Class practice sessions.
- Session create, switch, rename, and delete workflow.
- Per-session student records starting again at attempt 1.
- Session-aware Class charts and image-export titles.
- Schema v2 class/session data structure and automatic migration from earlier v4.3.x records.

### Changed
- Class record clearing applies to the current practice session only.
- Roster removal became non-destructive exclusion so historical records remain available.

## [4.3.3]

### Added
- Quick experiment name and common note.
- ΔEY / ΔTDS comparison in Quick and Class tooltips.
- Desktop coordinate preview for Quick target placement.
- Mobile tap interaction for points and target points.
- PNG chart generation with copy, save, share, and in-app preview fallback.

### Changed
- Chart exports include saved paths, live point, target point, goal guide, and legend while excluding transient hover / selection UI.

## [4.3.2]

### Changed
- Separated the current Quick input from committed saved attempts on the chart.
- Added a distinct live point and saved-to-live preview path.
- Quick main feedback now follows the current live input.
- Saved attempts receive their own dynamically recalculated target feedback.
- Goal guidance uses the live point first, then the latest saved point when no valid live point exists.

## [4.3.1]

### Changed
- Strengthened full-data export for restricted browser environments.
- Added visible JSON backup preview and clipboard-copy fallback.
- Uses the File System Access API for OS-level save dialogs when available.
- Avoids claiming a download succeeded when the browser may have blocked it.

## [4.3]

### Added
- Full JSON export / import for classes, students, records, instructor feedback, Quick data, profiles, and chart settings.
- `schemaVersion` for saved data.
- Storage-adapter layer to isolate persistence from calculation and UI logic.

### Changed
- Moved class administration into Settings.
- Replaced browser `prompt()` / `confirm()` dependencies with in-app dialogs.
- Preserved migration from earlier v4.x browser data.

## [4.2]

### Added
- Saved Quick attempts with automatic numbering and connected chart paths.
- Interactive Quick target point and target-relative guidance.
- Independent Quick and Class automatic-feedback controls.
- Multiple classes with independent rosters, records, notes, and instructor feedback.
- Migration from the earlier single-class structure.

## [4]

### Added
- Dynamic target classification badges for saved Class records.
- Separate brew notes and instructor feedback.
- Direction arrows between sequential Class attempts.
- Configurable extraction-yield and TDS chart bounds and tick intervals.
- Configurable brew-ratio line range and interval.
- Built-in **Classic Filter** profile plus user-defined brewing profiles.

### Changed
- Reorganized Settings into collapsible sections.
- Saved records are reinterpreted dynamically when target settings change.

## [3]

### Added
- Target-relative **STRONG / WEAK / UNDER / OVER** chart regions and combined corner regions.
- Hover details for chart points while retaining click-based detail view.

### Changed
- Replaced the earlier **Golden Cup** chart label with the neutral **TARGET** label while keeping the target range configurable.

## [2]

### Added
- Separate **Quick** and **Class** workflows.
- Student roster management and sequential per-student brew records.
- Brew notes and simple target-direction feedback.
- Class chart filtering and connected attempt paths.
- Browser-local persistence.

## Initial prototype

### Added
- Single-file browser calculator for dose, brew water, beverage mass, TDS, extraction yield, dissolved solids, and brew ratio.
- Automatic beverage-mass estimation when beverage mass is left blank, using a configurable liquid-retention value.
- Live brewing-control chart with extraction yield on the X-axis, TDS on the Y-axis, a default reference area, and brew-ratio lines.
