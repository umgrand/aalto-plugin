---
name: project-schedule
description: Review a design project in Aalto and export its schedule. Use when the user asks about a project's or room's budget, what has been ordered or delivered, what is still outstanding, or wants an FF&E schedule, spec list or lookbook as CSV, Excel or PDF.
---

# Review a project and export its schedule

## Find the project

Call `aalto_list_collections`. Collections form a tree: a project usually holds rooms as child collections. Match the user's words to a collection name and confirm when two names are close. Never guess an id.

## Report where the project stands

Call `aalto_get_collection_context` for the collection. It returns the budget roll-up, a count of products at each status, the sections, and a page of items. Use the cursor to read further pages of a large collection.

Answer the question the user asked, with numbers from the response:

- **Budget**: budget, total so far, and what remains. Aalto converts currencies; state the currency shown.
- **Status**: how many products are saved, shortlisted, ordered, delivered and installed.
- **Outstanding**: list the products not yet ordered (saved or shortlisted), with brand and price.

Products without a price are not in the total. Say how many there are instead of treating them as zero.

## Export

Call `aalto_export_collection` with the format the user asked for:

- `csv`: every plan.
- `xlsx` (an Excel spreadsheet) and `pdf` (a lookbook): paid plans.

The tool returns a download link that is valid for 15 minutes. Give the user the link and say when it expires. Exports are limited to 20 per person per day, and an export that fails still counts, so do not retry in a loop; report the error instead.

An export creates a file only. Nothing in the library changes.
