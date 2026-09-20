# Coffee Brewing Control

A local-first browser tool for coffee brewing education, repeated brew testing, comparative analysis, and optional direct TDS measurement from supported devices.

The application visualizes brew strength (TDS), extraction yield, and brew ratio relationships using the brewing control chart framework originating from E. E. Lockhart's work. It adds workflow features for quick iterative testing and classroom record keeping rather than reproducing a published chart as a static graphic.

## Features

- **Quick** — enter brew measurements, save and edit repeated attempts, compare changes, set a target point, and export the current chart as PNG.
- **Class** — manage classes, students, and reusable practice sessions; keep per-student attempts and instructor feedback.
- **Chart** — interactive TDS / extraction-yield chart with configurable target range, chart scale, brew-ratio lines, filters, and comparison paths.
- **Measurement Device** — optionally connect a supported refractometer and insert measured TDS directly into Quick or Class without changing the existing save / record workflow.
- **Profiles & presets** — save extraction targets as Target Profiles and chart scales / brew-ratio guides as Chart View Presets; the liquid-retention coefficient is managed independently in Calculation Settings.
- **Local-first storage** — records are stored in the browser; full JSON backup and restore are available.
- **Single-file app** — no build step, framework, external JavaScript library, webfont, image pack, or API key is required.

## Editing saved attempts

Quick history supports editing through the existing measurement form. An edit keeps the original attempt ID, position, and liquid-retention value. Saving or cancelling returns to the LIVE input that was present before editing. Unsaved edits are not committed records; reloading the page returns to the preserved LIVE input.

Class record edits preserve chart-filter selections. Instructor-feedback drafts remain in place during same-context screen refreshes; saving, cancelling, or changing the editing context ends the draft.

## Measurement device support

Version 4.4.0 introduces a reusable Measurement Device layer. The first supported profile is:

- **HM Digital BTR-1000 / RCM-1000BT**
- Transport: **Web Serial over Bluetooth Classic SPP**
- Tested with **Chrome on Windows and Android**

After selecting the HM Digital Device Profile in Settings, the app can connect to the device, show connection state in the header, and expose **Measure TDS** in Quick and Class.

A successful measurement replaces the current TDS input through the same input path used for manual entry. Measurement does **not** automatically save a Quick attempt or create a Class record. Existing TDS remains in place while a measurement is pending and is preserved if the device returns Air, Unstable, Hi Range, an unknown response, a timeout, or a connection error.

Measurement results are applied only while their original input context is still current. Switching students or edit targets, resetting the form, restoring a backup, or manually changing TDS invalidates the earlier application target. Simply repainting the screen or locking and unlocking it does not change that context.

Successful HM Digital responses are normalized at runtime into TDS, Brix, temperature, and refractive-index values. Version 4.4.0 uses TDS in the current brew workflow; the auxiliary values are retained only in runtime measurement results and are not added to brew records or backups.

### Connection setup

**Windows**

1. Turn on the refractometer.
2. If it does not appear in Chrome's device chooser, pair `BTR1000(Coffee)_xxxx` first in **Windows Settings → Bluetooth & devices**.
3. Return to Coffee Brewing Control and connect from Settings or the header device control.

**Android**

1. Turn on the refractometer.
2. If it does not appear in Chrome's device chooser, check **Android Settings → Apps → Chrome → Permissions → Nearby devices**.
3. Return to Chrome and connect again.

The operating system / Bluetooth stack may take some time to report a powered-off or sleeping Bluetooth Classic device as disconnected. The app updates its state when the browser reports the link loss and also handles transport failure if a measurement is attempted against a lost connection.

## Default reference profile

The built-in **Classic Filter** Target Profile starts with:

- Extraction yield: **18–22%**
- TDS: **1.15–1.35%**

These values are informed by published Specialty Coffee Association brewing materials and are provided as a starting reference only. Target ranges, chart scales, brew ratios, and liquid-retention assumptions are configurable and should not be interpreted as universal sensory-quality standards or physical limits.

When beverage mass is left blank, the application estimates beverage mass from brew water, measured TDS, and the configured liquid-retention value. The default liquid-retention coefficient is **2.1**, and it can be changed independently in Calculation Settings. Extraction-yield results therefore depend on the measurements and assumptions supplied by the user.

New Quick and Class records store the liquid-retention value used when they are saved. Editing a saved record continues to use that value, including a switch from manual to automatic Beverage. The global setting applies to new LIVE calculations, new records, and chart Brew Ratio guides; it does not change saved automatic-Beverage results. Target classification and feedback still follow the current target settings. Manual Beverage calculations do not use the retention coefficient.

Older records receive the dataset's configured retention value when migrated to schema v5, preserving their immediately preceding displayed results. This is a migration assumption, not a reconstruction of the coefficient originally used for each historical brew.

## Data and privacy

Brew records, class records, profiles, and settings are stored locally in the browser by the application. The application does not transmit entered brew or class data to an application backend.

When a supported measurement device is connected, communication is handled directly through browser device APIs. The selected Device Profile is saved with the app settings, but live serial-port objects and normalized auxiliary device readings are runtime-only. A successfully applied TDS value follows the normal Quick / Class data flow.

Hosting providers may still receive ordinary web-request metadata when the page itself is loaded.

## Backup and version compatibility

Version 4.4.1 uses **schema v5** with the existing browser storage key and JSON backup format identifier. Supported older data structures remain importable. JSON import validates the backup structure and settings before applying it; it does not add new TDS / extraction-yield range restrictions.

The app checks stored candidates before loading and preserves the previous committed snapshot as a recovery copy. If no valid copy can be read, or a newer schema is found, automatic writes stop to protect the stored data. In that condition, JSON export can preserve the raw candidates as a recovery-only bundle; this bundle is for inspection and is not a normal importable app backup.

Conflicting tabs stop automatic writes and retain their current in-memory content for export. Web Locks serialize participating tabs' writes where supported. Without that API, change detection remains available, but simultaneous writes cannot be fully coordinated. Session-only storage is temporary and should be backed up before closing the tab.

Before upgrading, export a JSON backup and close older app tabs that use the same browser storage. Older versions do not participate in the new write protection and should not be opened against migrated data. Keep the old application and its pre-upgrade backup if rollback is needed; schema-v5 backups are not intended for older versions.

## References

- E. E. Lockhart. *The Soluble Solids in Beverage Coffee as an Index to Cup Quality.* Coffee Brewing Institute, 1957.
- Specialty Coffee Association. *Coffee Brewing Control Chart*, Version 3, revised March 2019.

This project is independently developed and is **not affiliated with or endorsed by the Specialty Coffee Association**. No SCA logo or SCA chart artwork is included.

## Running locally

Open `index.html` in a modern browser.

Some browser features, especially direct clipboard image writing or device access on mobile local-file URIs, can be restricted by browser security rules. For mobile measurement-device use, serving the app over HTTPS such as GitHub Pages is recommended.

## GitHub Pages

The repository root can be published directly with GitHub Pages. `index.html` is the entry page.

Minimal repository structure:

```text
index.html
README.md
CHANGELOG.md
```

## Version

Current version: **v4.4.1**

See [CHANGELOG.md](CHANGELOG.md).

## License

No open-source license is selected in this repository template. Public source availability does not by itself grant reuse rights. If you want others to freely reuse and modify the code, add an explicit license such as MIT after deciding the terms you want.
