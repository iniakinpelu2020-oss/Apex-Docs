# Apex Docs

A rich document editor and PDF toolkit that runs entirely in the browser. Write, export a
real Word file, print to PDF, and merge or split PDFs — no server, no account, no upload.

**Status: built. It is one file, `index.html`. Open it and it works.**

## What it actually does

Writing:

- Headings, bold, italic, underline, strikethrough, bulleted and numbered lists, alignment,
  links, tables, quotes, clear formatting, undo and redo.
- Documents autosave to the device as you type, with a sidebar of everything you have
  written. The first line becomes the document's title.

Exporting:

- **`.docx`** — a genuine Word file built with `docx`, not HTML renamed. Headings, bold,
  italics, lists, numbering and tables survive, and Word opens it without the "different
  format" warning.
- **PDF** — through the browser's own print engine with a clean print stylesheet, so the
  text stays text. A canvas-based converter would have turned the document into a picture
  of a document.
- **`.html`** — a standalone web page of the document.

Importing:

- **`.docx`** through `mammoth`, which converts the real Word structure into editable HTML.

PDF tools:

- Merge any number of PDFs in the order you pick them.
- Extract pages, written as `2-5` or `1,4,9`.
- Split into single-page files, capped at 40 so a 300-page book does not bury you in
  downloads.

## What is deliberately missing

**Compression and signatures.** Compression that works needs a rasteriser or a server; the
naive JavaScript versions either make the file bigger or destroy its text layer. The honest
ways to shrink a PDF are to re-export it from the app that made it, or to print it to PDF
again. A digital signature needs a certificate, and a drawn image is not a signature any
bank accepts.

**Cloud sync and the in-app copilot.** Both need something outside this file: a Firebase
project, and the copilot's Worker route. The editor is written so either can be added
without restructuring, but neither is pretended to work — prompting for a login that does
not exist is worse than having no login.

## Known limits

- Documents live in the browser's `localStorage`, about 5 MB per browser. Export anything
  you care about; clearing site data clears the documents.
- The three libraries load from unpkg, so the first load needs a connection. Vendor them
  into the folder if you want it fully offline.
- Big PDFs are limited by the device's memory, not by this app. On an Android phone, keep
  single files under roughly 50 MB.

## How to run it

Open `index.html`. To put it online, upload that one file to Firebase Hosting, Netlify or
Cloudflare Pages — it is a static page, so nothing else is required.

## What you need to do

Nothing. No accounts, no keys, no card.

## Still to build, in order

1. Page thumbnails before splitting, so you can see what you are picking.
2. Images to PDF, and PDF to images.
3. Text extraction, which is the first step toward searching your own documents.
4. A service worker, so it installs as an app and works offline.
