# Coffee Brewing Control

A local-first browser tool for coffee brewing education, repeated brew testing, and comparative analysis.

The application visualizes brew strength (TDS), extraction yield, and brew ratio relationships using the brewing control chart framework originating from E. E. Lockhart's work. It adds workflow features for quick iterative testing and classroom record keeping rather than reproducing a published chart as a static graphic.

## Features

- **Quick** — enter brew measurements, save repeated attempts, compare changes, set a target point, and export the current chart as PNG.
- **Class** — manage classes, students, and reusable practice sessions; keep per-student attempts and instructor feedback.
- **Chart** — interactive TDS / extraction-yield chart with configurable target range, chart scale, brew-ratio lines, filters, and comparison paths.
- **Profiles** — save target, chart, ratio, and liquid-retention settings together.
- **Local-first storage** — records are stored in the browser; full JSON backup and restore are available.
- **Single-file app** — no build step, framework, external JavaScript library, webfont, image pack, or API key is required.

## Default reference profile

The built-in **Classic Filter** profile starts with:

- Extraction yield: **18–22%**
- TDS: **1.15–1.35%**

These values are informed by published Specialty Coffee Association brewing materials and are provided as a starting reference only. Target ranges, chart scales, brew ratios, and liquid-retention assumptions are configurable and should not be interpreted as universal sensory-quality standards or physical limits.

When beverage mass is left blank, the application estimates beverage mass from brew water and the configured liquid-retention value. Extraction-yield results therefore depend on the measurements and assumptions supplied by the user.

## Data and privacy

Brew records, class records, profiles, and settings are stored locally in the browser by the application. The application does not transmit entered brew or class data to an application backend.

Hosting providers may still receive ordinary web-request metadata when the page itself is loaded.

## References

- E. E. Lockhart. *The Soluble Solids in Beverage Coffee as an Index to Cup Quality.* Coffee Brewing Institute, 1957.
- Specialty Coffee Association. *Coffee Brewing Control Chart*, Version 3, revised March 2019.

This project is independently developed and is **not affiliated with or endorsed by the Specialty Coffee Association**. No SCA logo or SCA chart artwork is included.

## Running locally

Open `index.html` in a modern browser.

Some browser features, especially direct clipboard image writing, can be restricted when a local HTML file is opened through a mobile `content:` URI. The in-app image preview remains available, and browser-native image copy can be used where supported.

## GitHub Pages

The repository root can be published directly with GitHub Pages. `index.html` is the entry page.

Suggested minimal repository structure:

```text
index.html
README.md
CHANGELOG.md
```

A versioned snapshot such as `coffee_brewing_control_v4_3_5.html` can also be kept for release history if desired.

## Version

Current version: **v4.3.5**

See [CHANGELOG.md](CHANGELOG.md).

## License

No open-source license is currently selected for this repository. Public source availability does not by itself grant reuse rights. If you want others to freely reuse and modify the code, add an explicit license such as MIT after deciding the terms you want.
