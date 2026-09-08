# Rewrite state

## Current position

Pre-implementation planning is complete through I00, B00, B01, B02, B03,
B04, A0, and A1. No rewrite game process, daemon, watcher, Steam state, or
legacy source has been changed.

The next package is **B05: design integration**. It must resolve the finite
A1 contract gaps, freeze or explicitly defer the shared contracts and test
catalogue, and decide whether G1 may close. It must not begin implementation
or the browser feasibility probe until that work is complete.

## Continuation material

Detailed local evidence reports remain under `docs/rewrite/work/` and the
accepted planning baseline remains under `docs/rewrite/input/`. Both paths
are intentionally ignored because they can contain local operational details.
Read those reports before resuming B05.

The legacy BitBurner repository at commit `4ee272c` remains the protected
baseline. The rewrite repository is public but contains only sanitized source
and documentation; never commit saves, credentials, telemetry, live
accounting, endpoint details, or Steam-targeted configuration.

## Immediate resume sequence

1. Read `docs/rewrite/work/A1-foundation-contract-audit.md`.
2. Complete B05 from the I00–B04 and A0/A1 reports.
3. Record the G1 decision before assigning B05-P or implementation work.
