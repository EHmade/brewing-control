# Coffee Brewing Control

**Work toward the extraction targets you choose.** Coffee Brewing Control brings measurement, brew records, chart interpretation, and adjustment guidance together in a browser. It supports repeated personal testing and barista practice sessions, including student records and instructor feedback.

Use tasting and your own brewing goals to decide what to change. Target ranges are configurable references, not a verdict on flavor or quality. Notes are optional; the app does not automatically interpret tasting notes.

[Open Coffee Brewing Control](https://ehmade.github.io/brewing-control/) · [Changelog](CHANGELOG.md) · [Privacy & Data Handling](PRIVACY.md)

Current version: **v4.5.3 / schema v7**. Google ownership verification, live Cloudflare dashboard receipt, and published social-card checks are confirmed separately after deployment.

## Getting started

1. Open the page in a modern browser and choose **Quick** for repeated personal tests or **Class** for student practice records. No app installation or measurement-device connection is required for manual entry.
2. Enter dose, measured TDS, and at least one of brew water or beverage mass. The other mass can be estimated using the selected liquid-retention assumption. TDS must come from an actual measurement; the app does not measure it without a supported connected device.
3. Read the calculated result and chart relative to your selected target. Change the target in Settings when appropriate for your coffee and purpose. Save an attempt explicitly, make the next adjustment, and examine the change across records.
4. Export a JSON backup when you want to preserve or transfer records. They are stored in this browser, not a central user account.

Supported device access and image copy / sharing depend on the browser, operating system, and secure-context rules. Ordinary manual calculation does not require a connected refractometer.

## Features

- **Quick** — enter brew measurements, save and edit repeated attempts and per-attempt notes, estimate either missing brew mass, compare changes, set a target point, and export the current chart as PNG.
- **Class** — manage classes, students, and reusable practice sessions; keep per-student attempts and instructor feedback.
- **Chart** — interactive TDS / extraction-yield chart with configurable target range, chart scale, brew-ratio lines, filters, and comparison paths.
- **Measurement Device** — optionally connect a supported refractometer and insert measured TDS directly into Quick or Class without changing the existing save / record workflow.
- **Input review** — distinguish calculation validity from unusual but calculable brew data, retain the original result and classification, and acknowledge intentional outlier records.
- **Profiles & presets** — save extraction targets as Target Profiles and chart scales / brew-ratio guides as Chart View Presets; the liquid-retention coefficient is managed independently in Calculation Settings.
- **Local-first storage** — records are stored in the browser; full JSON backup and restore are available.
- **Independent core app** — the calculator, records, chart, and device logic run from index.html without a framework or external runtime library. Only the official hosted entry points request the optional Cloudflare analytics script. Social-preview and documentation assets are separate static files.

## Quick, Class, and Chart

**Quick** keeps a LIVE measurement form and saved attempts for repeated testing. Use a target point and chart paths to examine direction across attempts. The experiment name and common note are separate from per-attempt notes.

**Class** organizes classes, students, practice sessions, attempts, and instructor feedback. The collapsed context header identifies the current class, student count, and practice. Expand it to manage classes / students / sessions. Practice selection and creation live in the practice tab. The save button creates a record; simply entering values does not save a new attempt. Class charts show selected saved records, including an empty chart when no records have been added.

**Chart** brings TDS, extraction yield, brew-ratio reference lines, chosen targets, and record paths together. Chart Tools provides guide / goal controls, filters, and image export. Classification follows your current target settings rather than certifying flavor or quality. Display and chart-tool details are described below.

## Default reference profile

The built-in **Classic Filter** Target Profile starts with:

- Extraction yield: **18–22%**
- TDS: **1.15–1.35%**

These values are informed by published Specialty Coffee Association brewing materials and are provided as a starting reference only. Target ranges, chart scales, brew ratios, and liquid-retention assumptions are configurable and should not be interpreted as universal sensory-quality standards or physical limits.

When beverage mass is left blank, the application estimates beverage mass from brew water, dose, measured TDS, and the configured liquid-retention value. When brew water is left blank instead, it estimates brew water and Brew Ratio from directly entered beverage mass, dose, and TDS. If both masses are entered, both are used directly; if neither is entered, neither is estimated. The default liquid-retention coefficient is **2.1**, and it can be changed independently in Calculation Settings. Extraction-yield results therefore depend on the measurements and assumptions supplied by the user.

The two directions use the same mass-balance relationship, with masses in grams and TDS entered as a percentage:

    Beverage = (Brew water − Liquid retention × Dose) / (1 − TDS/100)
    Brew water = Beverage × (1 − TDS/100) + Liquid retention × Dose

Estimated brew water and its Ratio are marked as estimates. They provide a reference under the configured retention assumption rather than reconstructing extra liquid left in the dripper when brewing is stopped. Record cards and chart details identify the calculation source and the retention value used.

New Quick and Class records store the liquid-retention value used when they are saved. Editing a saved record continues to use that value, including a switch from manual to automatic Beverage. The global setting applies to new LIVE calculations, new records, and chart Brew Ratio guides; it does not change saved automatic-Beverage or automatic-Brew-water results. Target classification and feedback still follow the current target settings. EY calculated from directly entered Beverage does not use the retention coefficient; automatic Brew water and Ratio estimation still use it. Blank raw mass inputs remain blank in saved records and backups so an estimate is not mistaken for a direct input.

Records from before schema v5 receive the dataset's configured retention value during migration, preserving their immediately preceding displayed results. This is a migration assumption, not a reconstruction of the coefficient originally used for each historical brew.

## Input validity and review

A calculated brew result requires positive dose, brew-water and beverage values, finite derived values, and TDS strictly inside **0 < TDS < 100%**. Quick and Class show the accepted TDS interval beside the input. Values outside that interval can remain visible in the input field, but new records cannot be saved from them and they do not produce extraction yield, dissolved solids, classification, direction feedback, or chart points. Brew Ratio may still be shown when it can be calculated independently from dose and brew water.

Separately, the app evaluates calculable records for unusual mass relationships and extreme derived results. These records keep their existing values, target classification, and direction feedback while showing **입력값 확인**. After saving, the user can acknowledge that the record was entered intentionally; the record then shows **확인됨**. Changing dose, brew water, beverage, TDS, the input mode, or the retained coefficient clears that acknowledgment, while changing a Quick note or instructor feedback does not.

The acknowledgment is stored with the record. The review result and its internal reason codes are recalculated from the current evaluator rather than stored in the backup.

## Editing saved attempts

Quick history supports editing through the existing measurement form. An edit keeps the original attempt ID, position, and liquid-retention value. Saving or cancelling returns to the LIVE input that was present before editing. Brew water may remain blank for inverse estimation; editing keeps the saved liquid-retention value and preserves directly entered values. Unsaved edits are not committed records; reloading the page returns to the preserved LIVE input.

Each saved Quick attempt has an optional note edited directly on its card, independently of the measurement form. Click the note to edit it; save with the button or Ctrl/⌘+Enter, and cancel with the button or Esc. Unsaved notes survive same-context refreshes but are not committed by reloading the page. Saved notes appear in chart tooltips and details and are included in JSON backups. The experiment name and common Quick note remain separate. Individual Quick record deletion asks for confirmation.

Class record edits preserve chart-filter selections. Instructor-feedback drafts remain in place during same-context screen refreshes; saving, cancelling, or changing the editing context ends the draft.

## Display modes and chart tools

Split mode is the default: Quick and Class each open their corresponding chart, and the chart returns to the corresponding input screen. Empty Class charts are supported.

In Settings → 화면 표시 방식, integrated mode places Quick or Class inputs beside the chart with independent scrolling. The shared input-to-chart ratios are 35:65, 40:60 (default), and 45:55. A new integrated-mode selection requires a viewport of at least 1280 CSS pixels and at least 1200 pixels of workspace. Resizing does not overwrite a saved integrated preference: narrow screens show a warning, allow horizontal scrolling, and offer an explicit switch to split mode. A mode selected in Settings takes effect when leaving Settings.

입력 영역 크기 offers 기본 (Default) and 작게 (Compact), in either mode. Compact applies only at widths of at least 1024 CSS pixels with a hover-capable fine pointer. Touch and narrower screens use Default and disable the size controls without erasing the saved preference. The header and chart are not reduced by this option. Mode, ratio, and size are included in browser storage and JSON backups; older backups default to Split / 40:60 / Default. Older app versions may discard these new preferences when saving.

차트 크기 offers 한눈에 보기 (Fit to screen, default) and 크게 보기 (Large). Fit uses available height while preserving minimum readability; short screens or expanded controls may still require scrolling. Large uses available width up to the existing 840-pixel stage width and permits vertical scrolling. On narrow screens the two choices may have the same width. This setting works in both modes and on mobile, is saved in JSON backups, and returns to Fit after a full reset.

Chart Tools combines guide / target-point and student / attempt controls with image copy, PNG save, sharing, and a Chart / Target Settings shortcut. The shortcut scrolls to the relevant Settings sections without opening them. Collapsing Chart Tools hides its buttons, but keeps the summary and full out-of-range warning visible. Chart Tools and Class management can be toggled by clicking header text or empty space, with unboxed plus / minus indicators; other header buttons retain their own actions. Keyboard users can operate the native disclosure buttons. Image exports retain their existing geometry and exclude tooltips and coordinate previews, regardless of chart size.

## Measurement device support

Select a Device Profile in Settings to enable optional direct TDS measurement. Supported profiles are:

- **HM Digital BTR-1000 / RCM-1000BT** — Web Serial over Bluetooth Classic SPP; the existing Windows workflow and the supported Android Chrome workflow. Serial access / pairing support must be checked for the browser and OS.
- **DiFluid R2** — Web Bluetooth (BLE); tested with DFT-R102 firmware V219. Windows Chromium and Android Chrome were used for integration testing. Device access depends on browser and operating-system support.

The header shows connection state; Quick and Class expose the measurement button. A completed measurement fills the current TDS input through the normal input path. It does **not** automatically save a Quick attempt or create a Class record. Pending, failed, or incomplete measurements preserve the existing TDS.


### Connection setup

**HM Digital — Windows / Android**

1. Turn on the refractometer.
2. On Windows, if it does not appear in Chrome's chooser, pair **BTR1000(Coffee)_xxxx** in **Windows Settings → Bluetooth & devices** first.
3. On Android, check **Android Settings → Apps → Chrome → Permissions → Nearby devices** if the device is missing.
4. Return to the app and connect from Settings or the header control. The operating system may take time to report a powered-off Bluetooth Classic device as disconnected.

**DiFluid R2 — Windows / Android**

1. Turn on R2 and the computer / phone's Bluetooth. Use a browser that supports Web Bluetooth; an HTTPS or localhost origin is recommended for device access.
2. Choose the R2 Device Profile and connect from the app's device chooser. If another app or browser tab is using R2, disconnect it there first.
3. On Android, if R2 is missing, check **Android Settings → Apps → Chrome → Permissions → Nearby devices**. Depending on Android / Chrome version, location permission or the system location setting may also be required. Menu names vary; return to Chrome and retry after changing permissions.
4. If Auto / Count cannot be confirmed, open the R2 connection control at the top of the page and select **설정 다시 확인**.
5. If the app shows Disconnected while the device still shows a connection icon and R2 is absent from the chooser, close the chooser, power R2 fully off, wait for Disconnected in the app, power it on, and connect again. Check other apps / tabs if it remains unavailable. This is a recovery procedure; the rare mismatch's cause has not been established.

Successful auxiliary device readings remain runtime-only. They are not added to brew records or backups. The R2 profile selection and measurement-control visibility are saved; live connections and device Auto / Count are not app backup settings.

<details>
<summary>Detailed measurement behavior, input protection, and recovery</summary>

Results apply only while their original input context remains current. Switching Quick / Class, students, sessions, or edit targets, resetting the form, restoring a backup, or manually changing TDS cancels the earlier delivery. Returning to the same screen does not restore that permission. An already sent R2 measurement remains tracked and blocks another PC command until its lifecycle ends or the user explicitly reconnects. Cancelling delivery does not claim to stop the physical device. Simply repainting the screen or locking and unlocking it does not change the input target.

Normal numeric readings are preserved in the input, including values outside the brewing-calculation interval. This confirms delivery of the device-reported value, not its physical accuracy or suitability for brewing calculations. The existing **0 < TDS < 100%** calculation / record-saving rules still apply.

### DiFluid R2 settings and measurement

Click the connected R2 control or its settings icon in the header to open the existing settings popup. It shows confirmed model / firmware information and Auto / measurement Count. Connection reads the device settings without overwriting them; explicit user changes use device acknowledgment and readback. Auto / Count are locked while measuring. The app does not implement device calibration or firmware updates.

Device Count and PC measurement Count are shared: Count 1 requests Single, and Count 2–10 requests Average with that same Count. Device-button and Auto-initiated measurements can also fill the current Quick / Class input. Progress values remain previews; the app commits a final result once.

- **Device Average:** use the device's confirmed final average with complete progress and completion status.
- **Single, including temperature-stabilization Loop:** use the final reading.
- **Device-origin Auto ON, Count greater than 1, Single-to-Loop:** use the last N received Loop readings, where N is the captured device Count. If fewer than N are available, use the final Loop reading. This app-side averaging is not applied to PC / button Average or ordinary Single stabilization. If the device reports Average, its final average takes precedence.

Average completion cannot reuse an earlier running average when final data is missing. After completion status, insufficient final data receives a bounded 1.5-second additional wait; unresolved or detectably inconsistent data preserves the previous TDS and requires explicit reconnection. This interval is an application policy, not a guaranteed maximum device delay.

Start delay (20 seconds), silence after valid measurement activity (60 seconds), and a long measurement after actual Start (120 seconds) produce guidance. They do not declare completion, unlock a new PC measurement, or automatically retry. The nearby status offers **자세히** when appropriate; the existing popup offers **다시 연결**. Recovery first cancels old delivery and cleans up the connection, then reconnects and reads settings without automatically measuring.


</details>

## Data and privacy

Brew and class records, names, notes, feedback, profiles, and settings are stored locally in this browser. The app does not automatically upload them to an application backend or send them as analytics events. Device communication is direct through browser APIs; connections and auxiliary readings are runtime-only. User-requested export, copy, and sharing use the selected device or service.

The official HTTPS app entry points use **Cloudflare Web Analytics** for visits and page performance. This is separate from brewing records. The original app does not request that script on local files, localhost, other origins, or other project paths. Blocking or failing analytics must not prevent use of the core app. Cloudflare describes its beacon as not accessing browser storage; loading a third-party script is nevertheless a supplier-trust boundary, not a browser sandbox.

Google Search Console uses a verification meta tag for search / ownership management; no Google Analytics or Tag Manager script is added. Hosting and analytics providers may receive ordinary web-request information. See [Privacy & Data Handling](PRIVACY.md), also available as a [readable local page](privacy.html), for processing, retention, exports, choices, and public-contact guidance.

## Backup and version compatibility

Version 4.5.3 continues to use **schema v7**, introduced in v4.4.3, with the existing browser storage key and JSON backup format identifier. Supported schema-v1 through schema-v6 data remain importable. Schema v7 includes a strict boolean review-acknowledgment field on every saved Quick and Class record. Earlier records receive an unacknowledged state during migration without changing their stored brew measurements, water-input interpretation, notes, feedback, measurement-device settings, or retained liquid-retention value.

Application versions before v4.5.0 do not support the R2 profile even when they use schema v7. Versions before v4.5.2 may discard the newer display preferences. Keep a pre-upgrade backup and the previous application for rollback.


<details>
<summary>Detailed Import validation and resource limits</summary>

Current-schema representation is validated strictly, while supported historical shapes are handled by their migration contracts. In particular, early schema-v2 data may omit `excludedStudents`; malformed values remain rejected, and schema-v3-or-newer data retain their stricter requirement. Existing imported records with TDS outside the current calculated-result interval retain the original raw value but do not generate calculated brew results or chart points until edited to a valid TDS.

Backups are checked against Import resource budgets before they are applied. The file limit is **32 MiB** (33,554,432 bytes), checked before reading. After JSON parsing, the limits are **65,536 UTF-16 code units per string or object key**, **16,777,216 code units of combined text**, **250,000 entries per collection**, **3,000,000 structural values**, and **64 levels of nesting**. Excess data is rejected with an explanation rather than truncated. These are workload limits, not recommended classroom sizes or a promise that the browser can store the data. Recovery and pending snapshots also consume storage space; retain an external JSON backup, especially for large datasets.

Normalization keeps known Settings and Quick draft fields and discards unrecognized properties. Existing record values, notes, feedback, saved retention, and review acknowledgment remain subject to their existing compatibility contracts. The selected backup file remains unchanged if Import is rejected.


</details>

The app checks stored candidates before loading and preserves the previous committed snapshot as a recovery copy. If no valid copy can be read, or a newer schema is found, automatic writes stop to protect the stored data. In that condition, JSON export can preserve the raw candidates as a recovery-only bundle; this bundle is for inspection and is not a normal importable app backup.

Conflicting or stale tabs stop persistent mutations and retain their current in-memory content for read-only export. Full app-data reset uses a shared reset generation so participating tabs cannot restore queued, pending, primary, or recovery data from before the reset. Web Locks serialize participating tabs' writes and reset-generation changes where supported. Without that API, change detection remains available, but simultaneous operations cannot be fully coordinated. Session-only storage is temporary and should be backed up before closing the tab.

Before upgrading, export a JSON backup and close older app tabs that use the same browser storage. Versions before v4.4.3 do not participate in the reset-generation protection and should not be opened against migrated data. Keep the old application and its pre-upgrade backup if rollback is needed; schema-v7 backups are not intended for versions that use an older schema.

## Running locally

Open `index.html` in a modern browser.

Some browser features, especially direct clipboard image writing or device access on mobile local-file URIs, can be restricted by browser security rules. For mobile measurement-device use, serving the app over HTTPS such as GitHub Pages is recommended.

The original local app does not request Cloudflare analytics. The provided social-preview image, Privacy document, and sitemap are not required by the core calculator. Keep the documentation files together to use their local links.

## Deployment and public-site files

The official app uses GitHub Pages at https://ehmade.github.io/brewing-control/. The static site files are:

```text
index.html
README.md
CHANGELOG.md
COPYRIGHT.md
PRIVACY.md
privacy.html          # generated from PRIVACY.md; do not maintain a second copy by hand
social-preview.png    # original 1200 × 630 link-card image
sitemap.xml
```

Search metadata and the sitemap identify the single canonical app URL. Korean UI and English core terms do not imply a separate English-language page. No project-level robots.txt, application backend, account system, or hosting migration is added.

The issued Google verification meta tag stays in the head after verification. The Cloudflare client token is a public site identifier, not an API secret. The independent loader uses only the exact official HTTPS root / index.html paths and disables automatic SPA tracking; it does not read app state or emit custom events. Do not put the same token on unrelated projects.

Google ownership and sitemap submission, actual Cloudflare dashboard receipt, and public image / metadata responses must be checked after an authorized public update. Search indexing and the wording shown in search results or cached social cards are controlled by the respective services. Internal test details belong in the verification package, not this user guide.

## References

- E. E. Lockhart. *The Soluble Solids in Beverage Coffee as an Index to Cup Quality.* Coffee Brewing Institute, 1957.
- Specialty Coffee Association. *Coffee Brewing Control Chart*, Version 3, revised March 2019.

This project is independently developed and is **not affiliated with or endorsed by the Specialty Coffee Association**. No SCA logo or SCA chart artwork is included.

- J.-X. Guinard et al. *A new Coffee Brewing Control Chart relating sensory properties and consumer liking to brew strength, extraction yield, and brew ratio.* Journal of Food Science 88(5), 2023. DOI 10.1111/1750-3841.16531.

## Copyright & Usage

© 2026 Taehee Yoon. All Rights Reserved.

The hosted Coffee Brewing Control application may be used free of charge for personal, educational, research, and professional purposes, including use in cafés and paid instruction. An unmodified copy distributed by the copyright holder may also be run locally for the same permitted purposes.

Users may save, use, export, and share their own brewing records, backup JSON files, and chart images produced through the application's provided features.

Permission to use the application does not grant permission to reuse, modify, or redistribute its protected source code, interface implementation, documentation, or other protected project materials, except as permitted by applicable law or platform terms.

No exclusive rights are claimed over brewing principles, formulas, scientific concepts, or functional ideas. Referenced third-party materials remain subject to their respective rights. Third-party software, libraries, and other components used by this project remain subject to their respective licenses and terms.

See [COPYRIGHT.md](COPYRIGHT.md) for the full terms.
