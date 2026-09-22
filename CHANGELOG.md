# Changelog

All notable changes to Coffee Brewing Control are documented here.

The project was developed iteratively before its first public GitHub release. Earlier entries are intentionally condensed to major user-facing and architectural milestones rather than every intermediate test or debugging change.

## [4.4.2] - 2026-09-22

### Added
- Added automatic Brew water estimation in Quick and Class when Brew water is blank and Dose, Beverage mass, and TDS are provided. Estimated Brew Ratio is identified as an estimate.
- Added optional per-attempt Quick notes using the saved-card editor pattern from Class instructor feedback, with save / cancel and Ctrl/⌘+Enter / Esc shortcuts.
- Added Copyright & Usage terms clarifying free use of the hosted application and unmodified locally run copies distributed by the copyright holder, permitted use, export, and sharing of users’ own brewing records, backup JSON files, and chart images, restrictions on reuse of protected project materials, and the exclusion of brewing principles and third-party materials from ownership claims.

### Fixed
- Individual Quick attempt deletion now asks for confirmation before removing the record, matching Class record deletion.

### Changed
- Quick and Class records and chart details show whether Beverage or Brew water was estimated and the liquid-retention value used. Quick notes appear in chart tooltips and details.
- Shared raw-input reading, bidirectional mass calculation, and calculation-source presentation within the existing single-file app. The Quick measurement form does not add a note field.
- The forward automatic Beverage formula, default liquid retention of 2.1, existing manual-input policy, chart out-of-range notice, measurement transport, and PNG layout remain unchanged.

### Compatibility
- Advanced the saved-data schema to v6 to preserve each record’s Brew water input mode and Quick attempt note. Supported schema-v5 and earlier data remain importable; existing records retain their previous water-input interpretation and liquid-retention value.
- Automatic estimates remain derived values: blank raw inputs and the saved liquid-retention value are retained during editing and JSON backup / restore.
- The browser storage key and backup format identifier remain unchanged. Export a backup and close older app tabs before upgrading. Schema-v6 backups are not intended for older app versions.

## [4.4.1] - 2026-09-20

### Added
- Added editing for saved **Quick** attempts through the existing input form. Saving an edit preserves the attempt ID, order, and liquid-retention value; saving or cancelling restores the previous LIVE input.
- Added a per-record **liquid-retention snapshot** for Quick and Class so later Calculation Settings changes do not recalculate saved automatic Beverage values.

### Fixed
- Storage recovery now validates available candidates and falls back to a valid copy instead of silently replacing unreadable data with defaults. Recovery preserves the previous committed snapshot; unreadable or newer-schema data stops automatic writes.
- Added stale-tab write detection and serialized same-origin writes through Web Locks when available. Conflicting tabs keep their in-memory data available for JSON export instead of overwriting another tab.
- Class input ownership now follows student, class, practice-session, record-edit, and backup-restore transitions. Deleting the record being edited clears the obsolete form values.
- Delayed measurement results no longer replace input after its owner changes, an input reset, or a subsequent manual TDS edit. Returning to the same student does not reactivate an earlier measurement.
- Unsubmitted instructor feedback survives same-context Class re-rendering. Editing an existing Class record preserves chart-filter selections.
- Backup import now checks known data structures, record IDs, chart settings, and preset settings while retaining supported legacy migrations and historical roster records. Imported IDs are assigned through DOM properties rather than inserted into HTML attributes.
- File-save and JSON-copy actions now create a fresh export snapshot at the start of each operation. Backup restore also clears previous form, editing, and pending-measurement contexts.

### Changed
- Separated input updates and persistence from rendering, and extracted calculation functions with explicit settings. Quick input updates no longer rebuild the entire saved-attempt list.
- Shared Quick / Class measurement controls and separated Settings and Chart rendering responsibilities within the existing single-file app. Unapplied calculation, target, and chart fields survive unrelated Settings refreshes.
- Coalesced Quick input chart-render requests and flushes pending chart rendering before PNG generation. Added label associations for numeric fields and a chart description without changing the existing layout.
- The automatic Beverage formula, default liquid retention of **2.1**, manual-input policy, chart out-of-range notice, measurement transport, and PNG layout remain unchanged.

### Compatibility
- Advanced the saved-data schema to **v5**. Supported schema-v4 and earlier browser data / backups remain importable. Existing records receive the dataset's liquid-retention value during migration to preserve the results shown immediately before migration; this does not reconstruct an unknown historical coefficient.
- The legacy browser storage key **coffeeBrewControlClassroomV2** and backup format identifier **coffee-brew-control-backup** remain unchanged. Local / session storage and the memory fallback are retained.
- Web Locks strengthen coordination between participating v4.4.1 tabs. Environments without Web Locks retain change detection but do not guarantee protection against simultaneous writes. Older app tabs do not participate in the new coordination.
- Export a backup and close older app tabs before upgrading in the same browser storage context. Schema-v5 backups are not intended for older app versions; retain a pre-upgrade backup for rollback.

## [4.4.0] - 2026-09-19

### Added
- Added a reusable **Measurement Device** framework with persistent Device Profile settings and runtime-only connection / measurement state.
- Added direct HM Digital **BTR-1000 / RCM-1000BT** support through Web Serial and Bluetooth Classic SPP.
- Added **Measure TDS** actions to Quick and Class. Successful measurements enter TDS through the existing input path; measurements never auto-save a Quick attempt or Class record.
- Added a global header device control for connection state and reconnect, plus a Settings connection test that opens the device connection without sending a measurement command.
- Added platform-specific troubleshooting for Windows Bluetooth pairing and Android Chrome **Nearby devices** permission.
- Added normalized runtime measurement results for TDS, Brix, Celsius / Fahrenheit temperature, refractive index, and the original raw device response for future device-aware features.

### Changed
- Existing TDS remains visible while a measurement is pending and is replaced only after a successful new TDS result.
- Air, Unstable, Hi Range, timeout, unknown-response, and connection-loss cases preserve the previous TDS value.
- Measurement feedback now follows the current attempt and connection lifecycle: a new measurement replaces the previous result message, connection loss takes priority over an older measurement message, and a confirmed reconnect returns the measurement UI to standby.
- Connection and measurement state are handled independently, with guarded cleanup, duplicate-event protection, stale-port recovery, delayed-result rejection, and reconnect support after device sleep or link loss.
- Device Profile display names are used when a browser cannot expose the physical Bluetooth device name; the internal model can also accept a device-provided display name when available.

### Compatibility
- Advanced the saved-data schema to **v4**.
- Existing schema-v3 browser data and backups remain importable. Measurement-device settings default to **no device + controls hidden** for migrated data.
- The selected Device Profile and measurement-control visibility are included in normal app persistence and JSON backup; live serial-port objects and runtime measurement results are not persisted.
- The legacy browser storage key `coffeeBrewControlClassroomV2` and backup format identifier `coffee-brew-control-backup` remain unchanged.
- HM Digital device integration was validated with Chrome on Windows, a Windows PC using a Bluetooth dongle, and Android Chrome. Windows may require Bluetooth pairing before the device appears; Android Chrome may require **Nearby devices** permission.

## [4.3.6] - 2026-09-18

### Added
- Added an independent **Calculation Settings** section for the global liquid-retention coefficient, including the automatic Beverage mass-balance formula and an explanation of where the coefficient is applied.
- Split the former combined Brewing Profile into **Target Profiles** and **Chart View Presets**, each with built-in presets, load controls, and collapsible management for save / overwrite / delete.
- Added per-student master toggles to the Class chart filter, with aligned student-name columns and attempt checkboxes, so all attempts for one student can be selected or hidden at once while preserving mixed-selection state.
- Made the **Coffee Brewing Control** header title return to Quick as the app's home action.

### Changed
- Quick results now show the extraction target and Quick goal as separate reference lines; goal coordinates are no longer repeated inside the main feedback text.
- Quick goal feedback separates remaining ΔEY / ΔTDS from the adjustment recommendation for easier reading.
- Stabilized layout around Quick goal creation / removal and chart out-of-range warnings to reduce vertical shifts.
- Improved chart-header handling for long experiment / class / session names and constrained the mobile navigation pill to its content width while keeping its existing position.
- Renamed the UI setting from **absorption coefficient** to **Liquid retention** terminology while retaining the same calculation role.

### Compatibility
- Advanced the saved-data schema to **v3**.
- Existing schema-v2 browser data and backups remain importable. Legacy custom Brewing Profiles are migrated into same-named Target Profiles and Chart View Presets.
- During migration, the currently applied liquid-retention value is preserved as the global calculation setting; liquid retention is no longer stored per preset.
- The legacy browser storage key `coffeeBrewControlClassroomV2` and backup format identifier `coffee-brew-control-backup` remain unchanged for compatibility.

### Deferred / Future considerations — not implemented in v4.3.6
- Add stored-data size and record-count summaries in Settings if long-term classroom datasets make this useful.
- Move the `StorageAdapter` persistence backend from localStorage to IndexedDB if real-world data volume approaches localStorage limits; future native/app ports can use an appropriate backend such as SQLite.

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
