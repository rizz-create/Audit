# Audit Finalisation Suite

A single-window workspace that consolidates the four company-audit finalisation
documents so you upload the Winman JSON **once** instead of four times, review the
document-specific choices in one screen, and export each file to Word.

Live location (GitHub Pages): **https://marvandco.com/audit/**

## What's inside

| File | Role |
| --- | --- |
| `index.html` | The consolidated workspace — index sheet, single upload, tabbed document viewer, exports. |
| `documents/management-representation-letter.html` | Management Representation Letter (password gated). |
| `documents/agm-notice.html` | AGM Notice + attendance slips. |
| `documents/directors-report.html` | Directors' Report. |
| `documents/directors-shareholders.html` | List of Directors & Shareholders. |

The four documents in `documents/` are the **original files, unchanged**. The
workspace embeds each one in an iframe and drives it through the same file input
and export buttons the documents already have — so nothing about your document
wording or logic is altered.

## How it works

1. **Upload once.** Drop the ITR-6 JSON exported from Winman onto the dropzone.
   The workspace sets the file on every embedded document's own upload field and
   fires its existing load routine — so all four fill from one file.
2. **Shared fields.** The AGM number is shared between the AGM Notice and the
   Directors' Report, so you type it once. Everything else stays a per-document
   choice, made in that document's own panel inside its tab.
3. **Review & export.** Each tab shows the real document with its own input panel
   and live preview. Export a single document with "Export this to Word", or use
   "Export all four to Word" on the upload panel.

## Important — hosting

One-click "upload once, fill all four" needs the pages to be **same-origin**, which
they are on **GitHub Pages** (or any web server). If you open `index.html` by
double-clicking it straight from disk, the browser blocks the page from reaching
into the embedded documents; the workspace detects this and tells you. In that
case either:

- run a local server from this folder: `python3 -m http.server` then open
  `http://localhost:8000/audit/`, **or**
- upload the JSON inside each document tab — that always works.

The **Management Representation Letter is password-gated** by design. Unlock it in
its tab first; if you upload before unlocking, its reset-on-login clears the data,
so re-upload inside that tab after logging in.

When the JSON reaches the **Directors' Report**, that document shows its own
"Uploading JSON will clear all entered data — Continue?" confirmation (it always
has). Click **OK** to let it load.

## Trying it out

`sample-winman.json` in this folder is a dummy ITR-6 file you can drop onto the
dropzone to see all four documents populate before using a real audit export.

Nothing is sent anywhere — all reading and Word generation happens in the browser.
