# BCF Script Editor

A single-file, browser-based editor for writing, validating, and optimizing **Block Calculation File (`.bcf`)** scripts used in Maptek Vulcan block-model workflows.

> An independent tool for working with Vulcan BCF scripts — **not an official Maptek product or release.**

[![License: MIT](https://img.shields.io/badge/License-MIT-4D9D37.svg)](LICENSE)
&nbsp;·&nbsp; Single file · No build · Runs offline in any modern browser

**▶ [Try it live](https://jorge-sf.github.io/BCF_Editor/)** &nbsp;·&nbsp; or download [`BCF_Editor.html`](BCF_Editor.html) and open it in a browser.

<!-- Drop a hero screenshot or short demo GIF here — docs/demo.gif — this is what makes the repo (and a LinkedIn post) land. -->

---

## What it is

BCF scripts are plain-text files of conditional logic that assign values to block-model variables based on the values of other variables — grade classification, routing, NSR, and similar calculations. This editor gives that workflow a proper home: type-aware editing, live validation, in-browser simulation, and impact analysis, with **zero setup and no server**. It runs standalone in a browser tab, or embedded directly inside Vulcan's Internet Browser widget.

## Features

- **Type-aware editing** — reads a block-model header to drive validation and autocomplete against your actual variables.
- **Live validation** — inline squiggles and a diagnostics panel flag errors and warnings as you type.
- **Preview engine** — a full BCF interpreter that runs entirely in the browser, so you can simulate a script against sample values and see exactly which branches fire and which lines execute. Fast and offline; no round-trip to Vulcan.
- **Impact panel** — audits which variables a script reads and writes, and how blocks flow through its conditions.
- **Simplifier** — detects redundant or reducible logic and proposes cleaner equivalents, each backed by a Monte Carlo verification confirming the simplified version produces identical results across many random inputs.
- **Reference panel** — every BCF operator and function, documented inline.
- **Open / Save** — real file access via the File System Access API (`Ctrl+O` / `Ctrl+S`), with unsaved-change tracking.
- **Command palette & keyboard shortcuts** — power-user navigation throughout.

## Usage

### In the browser
Open the [live demo](https://jorge-sf.github.io/BCF_Editor/), or download `BCF_Editor.html` and open it locally. Everything runs client-side — nothing is uploaded, and it works offline.

1. Drag a `.txt` block-model header onto the editor to load your variable definitions.
2. Write or open a `.bcf` script (`Ctrl+O`).
3. Validate logic in the **Preview** panel, audit reads/writes in the **Impact** panel, and tidy up with the **Simplifier**.
4. Save back to disk with `Ctrl+S`.

### Inside Vulcan
Point Vulcan's Internet Browser widget at the local `BCF_Editor.html` file path. Because the app is a single self-contained file with no server dependency, it loads straight from disk and behaves the same as it does in a standalone browser.

## Architecture

The entire application — editor, interpreter, validators, panels, and styling — lives in one self-contained HTML file. That is a deliberate constraint: it has to load from a local `file://` path inside Vulcan's webview, with no bundler, server, or module loader at runtime. The only external reference is a web font, which degrades gracefully offline.

## License & attribution

Released under the [MIT License](LICENSE).

This project was developed while the author was working at [Maptek](https://www.maptek.com/) and has been approved for open-source distribution under the terms of the MIT license. Unless otherwise stated, copyright © 2026 Maptek Pty Ltd applies to all files in this repository, whether or not an individual file contains an explicit notice.
