# Rewrite documentation and test plan

Contract revision: B05/1. This public, sanitized index authorizes no game
effect, browser probe, daemon, watcher, or Steam work.

## Normative sources

| Subject | Source |
| --- | --- |
| Environment identity, ownership, capability boundaries and cash | [System contract](system-contract.md) |
| Observations, authority, controls, actions and manual state | [State/control contract](state-control-contract.md) |
| Immutable releases, activation, events and evidence | [Release/event contract](release-event-contract.md) |
| Independent cases, fixtures and gates | [Test catalogue](test-catalog.md) |

A shared term has one normative definition. Code may expose a defect or an
unknown, but cannot silently redefine these contracts. A change names evidence,
affected tests, invalidated claims and a new revision first.

## Evidence, ownership and gates

Claims are `implemented`, `locally-tested`, `integration-tested`,
`browser-confirmed`, `Steam-confirmed`, `historical-observation`, `assumed`,
or `unresolved`. A passing mock, PID, screenshot, source hash or file receipt
does not imply a stronger claim. The foundation integrator owns common
contracts; capability owners propose changes with requirement/test IDs.

G1 requires these documents and the independent A1 closure review. G2 is the
relevant T0–T3 implementation evidence. G3 is the named capability's browser
normal, failure, restart, pause/drain, owned-stop and unknown/rollback proof.
T4 is disposable browser, T5 protected-Steam inactive/shadow and T6 a named
authorized Steam effect. A lower layer never promotes a claim.

Before implementation, each capability document states behavior/units, initial
mode, operations/resource keys/freshness, unavailable/manual behavior, ROI,
migration/readback, independent cases, browser stop/rollback, authority-held
path and one bounded implementation increment.

Public source never includes saves, credentials, endpoint details, live account
values, private telemetry or Steam configuration. See the inactive
[operator guide](operator-guide.md) and [migration runbook](migration-runbook.md).
