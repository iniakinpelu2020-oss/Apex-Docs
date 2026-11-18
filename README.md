# Apex Docs

PDF and document tools that run entirely in the browser. Merge, split, rotate, compress,
sign, extract text.

**Status: not built. This is the easiest genuine win on the whole list.**

## Why this one is different

There is no backend, so there is nothing to keep alive and nothing to bill. The file never
leaves the device — which is also the honest privacy claim every "free PDF tool" website
makes falsely. Hosting is a static site, which Firebase Hosting gives you for free within
10 GB and ~360 MB a day.

Libraries that already do the work: `pdf-lib` (merge, split, rotate, page edits) and
`pdf.js` (rendering and text extraction). Both run in a browser tab.

## What to build, in order

1. Merge and split — the two things people actually need.
2. Rotate and delete pages.
3. Images to PDF, and PDF to images.
4. Text extraction, which is also the first step toward search later.

## The constraint that shapes it

A big PDF in a phone browser will run out of memory before it finishes. Do the work in a
Web Worker, show progress, and refuse files over a sensible size instead of crashing the
tab.

## What you need to do

1. Nothing. No accounts, no keys, no card.

## First three steps

1. A single page with a drag-and-drop zone and a merge button.
2. A split tool that shows page thumbnails you can pick from.
3. The same app installed as a PWA so it works offline.
