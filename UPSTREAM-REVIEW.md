# Review: persist cached tiles and avoid cache-triggered chart rescans

**Owner review only. No pull request or upstream issue has been submitted.**

Upstream: https://github.com/SignalK/charts-plugin
Base: `a7ad8dda7235f871c2df31ae214d43f3a10e67f2`

## Problem and proposed behavior

A tile write callback can run before a batch commits. Cache-file activity also triggers rescans, and rescans can replace working handles. The candidate serializes writes with per-tile commit behavior, drains writes on close, ignores working-cache/export watcher events and reuses working handles.

## Scope and decisions

Coordinate with existing worker-thread PR #155. This is a candidate extracted from the deployed local patch, not an instruction to submit it unchanged. Cache identifiers, tile coordinates and MBTiles locations do not change. A committed tile is not a guarantee against sudden power loss. Impit, proxy rotation and provider configuration are excluded.

## Validation status

The branch was prepared from current upstream source. Patch applicability and
diff whitespace checks are verified during preparation. These are review drafts,
not a claim of passing CI, deployment readiness or completed hardware validation.

## Before upstream submission

- [ ] Run included concurrent-write and independent-SQLite-reader regressions.
- [ ] Run included cache watcher, handle reuse, offline/rescan/restart regressions.
- [ ] Compare these cases with upstream PR #155; measure seeding throughput and event-loop latency before choosing a commit policy.

## Related upstream work

- https://github.com/SignalK/charts-plugin/pull/155

Keep boat identity, credentials, live data, custom release suffixes and deployment
scripts out of an upstream submission. Publish nothing to the parent until approved.
