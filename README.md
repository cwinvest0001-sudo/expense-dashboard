# Expense Dashboard

A single-page dashboard that answers one question at a glance: **where is the money going, and is anything moving in the wrong direction?**

## What it shows
- **Verdict strip** — total spend for the latest month, whether that's up or down versus the month before, and the fastest-growing category.
- **Monthly trend** — total spend over time, with the fastest-growing category overlaid so you can see what's pulling the total.
- **Category breakdown** — spending by category, largest first, with a marker on anything growing unusually fast (more than +50% versus the prior month).
- **Expense table** — every line item, filterable by category and month, and sortable by amount.

Calm, dark-on-light design with a single accent color reserved for "wrong direction" signals.

## The data
This dashboard runs on a small **sample dataset** built into the page for demonstration — it is not real financial data. All processing happens in your browser; anything you load stays on your device and is never uploaded.

## How the data is refreshed
Two ways:

- **Just to explore:** click **"Load new month's file"** and choose a CSV with the columns `Date, Vendor, Category, Amount, Notes`. The dashboard redraws instantly, entirely in your browser. The "Data through …" badge and every chart update from the file you pick.
- **To update the published site:** replace the CSV inside `index.html` — the block marked `id="seed"` near the bottom of the file — with the new month's rows, then commit and redeploy. Everything recalculates from whatever's in that block.

The dashboard always reports on the most recent month in the data and compares it to the month before, so include past months (a running year-to-date file is easiest).

## Running it locally
It's one self-contained HTML file — no build step, no dependencies, no server. Open `index.html` in any browser. To publish, deploy this folder as a static site (Vercel serves `index.html` at the root automatically).

## How it was built
Built by directing **Claude Code**, Anthropic's agentic coding tool: the layout, charts, data handling, and styling were specified in plain language and implemented by Claude, with the calculations verified against the underlying data.
