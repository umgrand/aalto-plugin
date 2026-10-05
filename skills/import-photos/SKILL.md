---
name: import-photos
description: Turn photos into Aalto products. Use when the user shares photos from a showroom, a site visit, a trade fair or a catalogue and wants them saved as products in their library.
---

# Import photos as products

Needs read and change access. Up to 50 photos per import, each a JPEG, PNG, WebP or GIF of at most 10 MB. Convert HEIC photos to JPEG first.

## 1. Look at each photo

For every photo, note what can actually be seen: a product name or model on a label, the brand, the product type (chair, pendant, tile and so on) and the colour. Leave a field empty when the photo does not show it. Do not guess prices or dimensions.

## 2. Start the import

1. Find the target collection with `aalto_list_collections`, or create one with `aalto_organize`. Imports only go into a private collection, not one that is shared by link or published.
2. Call `aalto_import_photos_start` with one entry per photo and the details from step 1. It returns an upload slot for each photo.

## 3. Upload

- If files can be uploaded from here, send each photo to its slot as the tool's response describes.
- If not, give the user the `upload_page_url` from the response. They open it in their browser, signed in to Aalto, and drop each photo onto its slot.

Wait until the user says the photos are uploaded.

## 4. Preview and show the summary

Call `aalto_import_photos_preview`. Show the user the products that will be created, the name proposed for each photo, and anything that could not be read. Ask whether to go ahead.

## 5. Commit

After the user approves, call `aalto_import_commit` with the confirm token from the preview. If it answers `in_progress`, wait about a minute and call it again with `resume: true`.

Report how many products were created and where. Photo imports do not use AI product imports. The import can be reviewed and undone in Aalto under Settings → MCP → AI activity.
