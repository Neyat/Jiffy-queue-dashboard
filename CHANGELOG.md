# Changelog

All notable changes to the JiffyShirts SLA Dashboard.

## [1.0.0] — 2026-04-22

Initial locked-in version.

### Current State layer
- Total in queue with New / Open status breakdown
- New In Today / Yesterday with explicit date labels (CST)
- Service Level %, SLA Breached, Oldest Ticket
- Priority buckets (SLA-based age ranges)
- Volume by Requested Date chart
- Issue Type breakdown (chart + detail table with sums)
- New Tickets by Date daily totals table
- Snapshot-age pill (red when data is >30 minutes stale)
- Data-range, load-time, and calculation-time timestamps

### Comparison layer (two-CSV mode)
- **Worked** computed as set-difference on ticket IDs — true "left the queue" count, not activity noise
- New Arrivals since previous snapshot
- Net Queue Change (Current − Previous)
- Previous Queue Size
- Time span between snapshots (hours + minutes)

### UX / Honesty upgrades
- Locked timezone to CST/CDT (all comparisons and displays)
- Fixed timestamp parsing bug that was incorrectly shifting early-morning tickets to the previous day
- Removed misleading "Updated" / "Worked" / "Resolved" single-snapshot cards
- Clear explanatory legend in the data-snapshot banner
- Hint card prompts user to upload a previous snapshot for comparison features
