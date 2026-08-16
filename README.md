# Stamp Room — PDF Watermark Studio

A single-file, browser-based tool for adding watermark text and stamps to PDF documents — no server, no database, no upload to any third party. Everything runs locally in your browser tab.

## Why

Marking PDFs with labels like `CONFIDENTIAL`, `DRAFT`, or `FOR INTERNAL USE ONLY` usually means opening a separate PDF editor and reconfiguring the same font, position, and styling every time. This tool turns that into a few clicks, with reusable templates for watermarks you apply often.

## Features

- **Drag-and-drop PDF upload** with live page preview
- **Custom watermark text** — font (Helvetica / Times / Courier), size, bold/italic, color, opacity
- **Horizontal lines** above and below the text, with adjustable color, thickness, length, gap, and opacity
- **Optional background highlight** behind the watermark
- **Flexible positioning** — 7 presets, or drag the stamp directly on the page preview
- **Rotation** for diagonal stamps (e.g. a classic angled `CONFIDENTIAL`)
- **Page selection** — all pages, first page, last page, or a custom range (`1, 3, 5-10`)
- **Saved templates** — save a configuration once, reuse it on future documents; comes with a few starter templates (Internal Use, Confidential, Review, Company Copy)
- **Dynamic fields** — `{{COMPANY}}` and `{{RECIPIENT}}` prompt for a value at generation time; `{{DATE}}` and `{{DOCUMENT_NAME}}` fill in automatically
- **Session history** — re-download anything generated earlier in the same tab
- **Original file untouched** — a new PDF is generated (`yourfile_Stamped.pdf`); nothing overwrites the source

## How it works

The app is a single HTML file. All PDF handling happens client-side:

- [PDF.js](https://mozilla.github.io/pdf.js/) renders the uploaded PDF for on-screen preview
- [pdf-lib](https://pdf-lib.js.org/) writes the watermark (text, lines, background) into a new PDF and produces the downloadable file

No backend, no database, no file storage — the PDF never leaves your browser.

## Usage

1. Open `pdf-watermark-studio.html` in a modern browser (Chrome, Edge, or Firefox).
2. Drop in a PDF or click to browse for one.
3. Set your watermark text and styling in the right-hand panel (Text / Lines / Position / Pages tabs).
4. Drag the stamp on the preview or pick a preset position.
5. Choose which pages it applies to.
6. Click **Generate PDF** — the stamped file downloads automatically.
7. Optionally save the configuration as a template for next time.

No installation or build step required — just open the file.

## Limitations

- Templates and history are kept only for the current browser tab/session; they're not saved to disk or synced anywhere.
- Watermarking currently applies one style/config across the selected pages per generation run (not different watermarks on different pages in a single pass).
- Fonts are limited to PDF's built-in standard fonts (Helvetica, Times, Courier); custom font uploads aren't supported.
- The on-screen preview uses web fonts as a close visual approximation of the generated PDF fonts — minor spacing differences are expected.
