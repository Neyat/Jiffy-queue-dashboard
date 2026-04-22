# JiffyShirts Service Level Dashboard

A single-file HTML dashboard for monitoring the JiffyShirts customer support queue. Upload Zendesk CSV exports to see queue health, SLA status, volume trends, issue-type breakdown, and (with two snapshots) a true "tickets worked" comparison.

## Features

**Current State layer** (always shown, from one CSV):
- Total in queue with New / Open breakdown
- New tickets in: today, yesterday, by date
- Service Level %, SLA breached, at-risk, oldest ticket
- Priority buckets (SLA-based age ranges)
- Issue type breakdown (counts, percentages, chart)

**Comparison layer** (when a second "previous" snapshot is uploaded):
- **Worked** = tickets present in previous snapshot but removed from current = true "left the queue" count (resolved / closed / merged). Not inflated by auto-replies, macros, or customer activity.
- New Arrivals since previous snapshot
- Net queue change
- Time span between snapshots

**Honest labels:**
- Snapshot-age pill turns red when the data is more than 30 minutes old
- All times in CST/CDT (JiffyShirts account timezone)
- Explanatory legend explains what every number means

## Usage

1. Export from Zendesk: **Views -> All tickets / All queues -> CSV export**
2. Open the dashboard (the deployed URL or `index.html` locally)
3. Drag the CSV into the **Current snapshot** upload zone
4. (Optional) Upload an earlier export into the **Previous snapshot** slot to enable "Worked" comparison
5. Click **Recalculate** to refresh numbers with the current time (useful for SLA status)

## Workflow tip: true "worked today" counts

Export a snapshot first thing in the morning and save it (e.g., `queue-2026-04-22-0600am.csv`). When you want a progress check later in the day, export again and load both — the comparison layer tells you exactly how many tickets left the queue between them.

## Deployment

The dashboard is a single `index.html` file with no build step. Any static host works:

- **GitHub Pages** — enable in Settings -> Pages after pushing to a repo
- **Netlify** — drag-and-drop deploy, or connect the GitHub repo for auto-deploy
- **Local** — just open `index.html` in a browser

All processing is client-side. No data leaves the browser; CSVs are parsed in JavaScript.

## Tech

- Vanilla HTML + JS (no framework)
- [PapaParse](https://www.papaparse.com/) for CSV parsing (via CDN)
- [Chart.js](https://www.chartjs.org/) for charts (via CDN)
- No backend, no storage, no cookies

## Changelog

See `CHANGELOG.md`.
