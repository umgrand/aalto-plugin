# Aalto plugin

Aalto is a product-sourcing workspace for interior designers, architects and creative studios. This plugin connects an AI app to your studio's Aalto library, so you can search, save, import and export products in a conversation.

It works in ChatGPT and Codex, and in Claude (claude.ai, the desktop app, Cowork and Claude Code).

## What you can ask

- "Find warm oak dining chairs under $1,500 in my library."
- "What is still not ordered for the Dining Room, and how much budget is left?"
- "Save this supplier page to my Kitchen project."
- "Turn this spreadsheet into products in a new project called Hotel Lobby."
- "Here are 12 photos from the showroom. Add them to Sourcing Trip."
- "Export the Living Room as an Excel schedule."

## What is in the plugin

| Part | What it does |
|---|---|
| Aalto connector | Points at Aalto's hosted server, `https://aalto.app/mcp`. You sign in to Aalto and approve the app. |
| `get-started` skill | Checks the connection and explains what your access level allows. |
| `source-products` skill | Searching, alternatives, saving from a link, adding to projects and changing status. |
| `import-spreadsheet` skill | Importing a CSV or Excel file, with a preview you approve before anything is written. |
| `import-photos` skill | Turning photos into products, with a preview you approve first. |
| `project-schedule` skill | Budget and order status for a project, and CSV, Excel or PDF export. |

The plugin contains instructions and a server address only. It runs no code on your computer, installs no packages and stores no credentials.

## Requirements

- An Aalto account on the Pro plan. See https://aalto.app/pricing.
- A workspace admin turns AI access on in Aalto under Settings → MCP and chooses **Read only** or **Read and change**.

## What it sends and where

Every request goes to `https://aalto.app/mcp`, which is Aalto's own server, and signs in through Aalto's sign-in page. The AI app receives the products, collections, tags and custom fields of the workspace you are signed in to, and nothing from your account, billing, sharing or usage data.

When you ask it to save a supplier link, Aalto's server reads that web page to fill in the product's details. When you import a spreadsheet or photos, the file is uploaded to Aalto.

## Safeguards

- It never deletes products or collections.
- It never changes sharing, publishing, billing or account settings, and cannot add to a board that is shared by link or published.
- Bulk edits and imports show a preview and wait for your approval.
- Every action is logged in Aalto under Settings → MCP → AI activity, where you can see what changed and undo it.
- You can limit or switch off each connected app in Aalto at any time.

## Support

https://aalto.app/support or support@aalto.app. Privacy policy: https://aalto.app/legal/privacy.
