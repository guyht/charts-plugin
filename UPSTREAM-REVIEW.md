# Review proposal: optional browser-profile HTTP transport for chart requests

**Owner review only. No pull request or upstream issue has been submitted.**

Upstream: https://github.com/SignalK/charts-plugin
Base: `a7ad8dda7235f871c2df31ae214d43f3a10e67f2`

## Problem and proposed behavior

A browser-profile HTTP client can provide cookies and consistent request behavior for authorized chart services that do not interoperate with the normal server fetch. The current local implementation replaces fetch globally; decide whether upstream wants an opt-in transport before implementing that interface.

## Scope and decisions

The attached patch is the current mandatory-client implementation for discussion ONLY; it is not an implemented optional transport. Native impit deadlines bound headers/bodies, cross-origin redirects strip credentials, and TLS verification remains enabled. No Webshare configuration, IP cycling, credentials, provider URLs or cache changes are included.

## Validation status

The branch was prepared from current upstream source. Patch applicability and
diff whitespace checks are verified during preparation. These are review drafts,
not a claim of passing CI, deployment readiness or completed hardware validation.

## Before upstream submission

- [ ] Run the included header, cookie, redirect, timeout, error-redaction and token tests.
- [ ] Design an opt-in setting that leaves existing providers on the current transport by default.
- [ ] Verify Linux ARM64 binary support, installation behavior, cookie isolation and fallback/error behavior.

Keep boat identity, credentials, live data, custom release suffixes and deployment
scripts out of an upstream submission. Publish nothing to the parent until approved.

## Preparation results — 6 November 2026

Reference patch applies cleanly to the recorded upstream base, with custom release suffixes removed. It is a discussion artifact; no optional transport setting has been implemented or newly tested.
