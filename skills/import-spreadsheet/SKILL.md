---
name: import-spreadsheet
description: Import a spreadsheet of products into Aalto. Use when the user has a CSV, an Excel file, a supplier price list or an existing FF&E schedule they want turned into Aalto products.
---

# Import a spreadsheet into Aalto

Needs read and change access. An import always goes start → preview → the user approves → commit. Never commit without showing the preview.

## 1. Learn the format

Call `aalto_describe_schema`. It lists the standard and custom fields, the valid product types and statuses, and the columns of the import template.

## 2. Prepare a CSV

- Aalto imports CSV, up to 5 MB and 2,000 rows. Convert an Excel file to CSV first.
- Map the user's columns to the template's columns. Keep the user's values as they are; do not invent prices, brands or dimensions for empty cells.
- If a column has no obvious match, ask the user, or leave it out and say so.

## 3. Start and upload

1. Find the target collection with `aalto_list_collections`, or create one with `aalto_organize` if the user asked for a new project. Imports only go into a private collection, not one that is shared by link or published.
2. Call `aalto_import_start`. For a small file, pass the CSV text inline. Otherwise it returns a signed upload URL that is valid for 2 hours.
3. Upload the CSV to that URL exactly as the tool's response describes (an HTTP PUT with content type `text/csv`).

## 4. Preview and show the summary

Call `aalto_import_preview`. Show the user, in plain words:

- how many rows will become products,
- which columns were mapped to which fields,
- duplicates of products already in the workspace,
- rows with errors and why,
- the quota lines: how many products and AI product imports the import will use, and whether any link-only rows will be imported without details.

Ask whether to go ahead. If the user wants changes, fix the file and start again.

## 5. Commit

After the user approves, call `aalto_import_commit` with the confirm token from the preview.

- If it answers `in_progress`, wait about a minute and call it again with `resume: true`.
- If it answers `conflict`, something changed since the preview. Run the preview again and show the new summary.
- Finish by reporting how many products were created, how many rows were skipped and why, and the collection they went into.

Imported rows go into the chosen collection. The import can be reviewed and undone in Aalto under Settings → MCP → AI activity.
