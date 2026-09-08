# Rewrite state and control contract

Contract revision: B05/1. All records use the environment envelope in the
[system contract](system-contract.md).

## Authority and controls

`AuthorityGrant` is an external operator-registry record containing grant ID,
envelope, issuer/evidence, issue/not-before/expiry times, grant/revocation
revisions, capability, exact operations, resource scopes, limits, stop rule
and verification receipt. Omitted money/RAM/quantity/duration/rate limits mean
zero permission. Only authenticated operator authority or explicitly delegated
existing scope may issue/amend/renew it. Source, synced config, proposal,
desired state, historical prose and AI may only narrow authority. Missing,
expired, revoked, forged or envelope-mismatched grants deny.

Desired state is revisioned and contains preferences, typed expiring overrides,
pause, selected release, actor and reason. Commands carry immutable command ID,
expected revision, caller, operation, payload, deadline and correlation ID.
Local and game clients receive the same validation/revision. Conflict and
unknown schema/key/enums reject. Precedence: emergency pause; authority
restriction; manual override; temporary override; durable preference; base
policy. Selecting a release or requesting `act` does not issue authority.

## Actions

Actions carry logical idempotency key, attempt ID, envelope, capability,
operation, proposal digest, desired revision, grant/revocation refs, input
digests, required leases/fences/reservations, timing, cooldown, budgets and
reconciliation rule. Lifecycle is `proposed → accepted → started → completed`,
or `denied|expired|cancelled|failed-no-effect|unknown`. Persist acceptance,
revalidate and persist `started` before one API invocation. Crash/uncertain
result after start is unknown and cannot blindly retry. Exact duplicates return
their receipt; changed payload under the same logical ID rejects. Pause blocks
new effects; drain permits only already-started work; owned stop grants neither
exit/liquidation nor manual-action cancellation.

## Observations and manual state

Observations include producer boot nonce/monotonic sequence, envelope, units,
value or unavailable reason, collection time, receiver monotonic receipt time,
source/process/release identity and digest. Older sequences cannot replace
newer; byte-different duplicate sequences are faults. Missing, NaN, stale,
reordered, wrong-epoch or inconsistent inputs deny/re-observe, never zero-fill.

Identity/grant/control/fence, process/RAM, cash/price/fee/position, CCT, host,
DNET and HACK rows require ≤1 s input age and ≤100 ms collection skew;
manual/terminal/GO require ≤250 ms and ≤100 ms skew. Re-read every mutable
precondition immediately before an API call. Any changed input invalidates the
accepted intent. Read-only health may be 5 s old but displays stale/unknown.

Manual/foreign ownership is the default; matching desired work proves nothing.
Only accepted action, valid lease and causal post-call observation establish
rewrite ownership. Unavailable state, lost provenance, manual-use signal,
unexpected change or restart pauses automation and preserves reality. Resume
needs fresh explicit relinquishment. `manualHold` always narrows authority.
Backdoor actions hold a composite player/terminal lease, record start location,
verify each hop, and restore only while authority, provenance and lease remain
valid; they never silently connect home.
