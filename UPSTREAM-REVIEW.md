# Review proposal: expose documented per-provider cache statistics

**Owner review only. No pull request or upstream issue has been submitted.**

Upstream: https://github.com/SignalK/charts-plugin
Base: `a7ad8dda7235f871c2df31ae214d43f3a10e67f2`

## Problem and proposed behavior

An instrument integration currently needs an internal Charts module to read hit/miss counters and filesystem knowledge to measure cache footprint. A documented per-provider statistics interface would remove this brittle coupling and benefit any chart provider.

## Scope and decisions

No new production implementation is included. Generalize provider IDs rather than publishing sonar-only paths as core behavior. The existing boat adapter and instruments stay separate. Browser-cache hits never reach the server.

## Validation status

The branch was prepared from current upstream source. Patch applicability and
diff whitespace checks are verified during preparation. These are review drafts,
not a claim of passing CI, deployment readiness or completed hardware validation.

## Before upstream submission

- [ ] Agree on a stable API with upstream before adding implementation.
- [ ] Specify counter reset behavior, failed-download semantics, file bytes versus tile payload, WAL/SHM accounting and stale/unavailable status.
- [ ] Check existing statistics endpoints before adding another one; prefer extending a suitable interface.

Keep boat identity, credentials, live data, custom release suffixes and deployment
scripts out of an upstream submission. Publish nothing to the parent until approved.
