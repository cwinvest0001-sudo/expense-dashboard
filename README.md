# Expense Dashboard

A one-page dashboard that answers one question at a glance:

> **Where is our money going, and is anything moving in the wrong direction?**

It's a single self-contained HTML file. There's no server, no database, no tracking and no outside libraries. Everything runs in your browser.

---

## What it shows

1. **Verdict strip.** Three numbers you can read in two seconds:
   - total spend for the latest month
   - the change versus the month before, marked **Better** (green) or **Worse** (rust)
   - the fastest-growing category, tagged *Unusually fast* if it jumped more than 50%
2. **"Before relying on these numbers."** An honesty check that runs automatically. It lists anything that makes the figures less certain, including:
   - expenses with no amount
   - possible duplicate charges
   - notes like "reimbursed?" or "check w/ finance"
   - a month that looks incomplete

   Each item links to the exact rows behind it.
3. **Monthly trend.** Total spend as a bold line. The fastest-growing category is shown as a shaded area underneath, so you can see how much of the total it takes up. Hover over any month for exact figures.
4. **Where the money goes.** Categories from largest to smallest. Anything rising unusually fast is highlighted.
5. **All expenses.** Every line item. You can filter by category, by month, or to only the rows with data notes, and sort by amount or date. A running total at the bottom updates as you filter.

**Design rules:** dark text on a light background, generous spacing, and no chart clutter. Color carries meaning:
- **rust** means something is moving the wrong way
- **green** means total spending fell
- **slate gray** means "double-check this data"

---

## The data

The page ships with a small **sample dataset** (January–June 2026) so it has something to show. It is illustrative, not real company financials.

---

## How the data gets refreshed

**For anyone viewing the page:** click **"Load new month's file"** and choose a CSV with these columns:

```
Date, Vendor, Category, Amount, Notes
```

The whole dashboard recalculates instantly: the verdict, the charts, the data checks and the table. The file is read **only inside your browser**. It is never uploaded anywhere, and it's gone when you close the tab. Include earlier months, not just the new one, so there's a previous month to compare against.

**To update the published site itself:**
1. Open `index.html`.
2. Find the block marked `id="seed"` and replace the CSV rows inside it with the new data.
3. Commit the change to this repository. Vercel redeploys automatically.

The dashboard always reports on the most recent month in the data. The "Data through …" label at the top and bottom shows which month that is.

---

## Running it yourself

Download `index.html` and double-click it. It works in any modern browser, fully offline. To host it, deploy this repository as a static site. Vercel serves `index.html` at the root with no configuration.

---

## How it was built

This dashboard was built by **directing Claude Code**, Anthropic's AI coding assistant, in plain language: no code was written by hand. The owner described the question the dashboard should answer, the layout, the design standard and the honesty requirements. Claude planned it, built it, tested it in a browser, and checked the calculations against the underlying data.
