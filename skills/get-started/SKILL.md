---
name: get-started
description: Set up and check the Aalto connection. Use when the user has just installed Aalto, asks what Aalto can do here, or an Aalto tool was refused with a permission or sign-in error.
---

# Get started with Aalto

Aalto is a design studio's shared product library: products saved from supplier websites, organised into collections (projects and rooms), with budgets, statuses and schedules.

## Check the connection

1. Call `aalto_whoami`. It returns the signed-in person, the active workspace, their role, the access level and the plan limits.
2. Tell the user which workspace is connected and what the access level allows:
   - **Read only**: search, read products and collections, find similar products, export.
   - **Read and change**: also save, create and edit products, organise collections, and import spreadsheets and photos.
   - **Off**: nothing. A workspace admin turns access on in Aalto under Settings → MCP.
3. If the call fails with a permission error that mentions Aalto Pro, say that connecting AI apps is part of the Pro plan and point to https://aalto.app/pricing.

## What to suggest next

Offer two or three things that fit the access level, in the user's own terms:

- "Find warm oak dining chairs under $1,500."
- "What is still not ordered for the Dining Room?"
- "Save this supplier page to my Kitchen project." (needs read and change)
- "Turn this spreadsheet into products." (needs read and change)
- "Export the Living Room as an Excel schedule."

## What Aalto never does through this connection

- It never deletes products or collections.
- It never changes sharing, publishing, billing or account settings.
- It cannot add to a collection that is shared by link or published.

If the user asks for one of these, say it has to be done in Aalto itself at https://aalto.app.

## Where changes can be reviewed

Every action is recorded in Aalto under Settings → MCP → AI activity, where the user can see what changed and undo it.
