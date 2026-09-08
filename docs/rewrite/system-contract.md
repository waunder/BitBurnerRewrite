# Rewrite system contract

Contract revision: B05/1. Initial mode is `observe` or `propose`; SHARE is
paused and STOCK execution is inert. Scope is not authority to act.

## Environment envelope

Every observation, command, grant, lease, reservation, receipt, action and
event carries schema version, contract revision, immutable ID and an envelope:
`environmentClass` (`browser-test` or `steam-protected`), external
`registrationId`, in-save `saveMarker`, externally registered `saveEpoch`,
admitted `sessionId`, and observed `gameBuild`. Class equality is insufficient.
Private registration binds expected installation/profile, adapter root, source
channel, archive root, bootstrap digest and current envelope; it is neither
synced configuration nor a game secret.

Admission compares private expectations, observed marker/reset identity and a
fresh session challenge before any target write or process start. Unknown or
mismatched identity records a refusal outside the target and denies target
writes. Clone, import, reset uncertainty, reload or sequence rollback creates
a new registration/epoch: old grants, controls, leases, reservations and
executable requests are inert. This is cooperative detection, not a sandbox
against arbitrary game scripts.

## Shared ownership

One admitted in-game arbiter serializes effect attempts and leases. Local/game
controls and capability modules submit requests; none is another reconciler.
Lease identity contains envelope, resource slice, owner generation, arbiter
incarnation, persisted monotonic per-resource fence, expiry, limits, renewal,
parent and release receipt. A stale/revoked/expired fence blocks all new
effects and spawns.

Transfer fences and drains the old owner, observes attributable work complete
twice one heartbeat apart, writes a release receipt, then issues a higher
fence. Foreign, partial, legacy-relaunched or ambiguous-PID work blocks
transfer and is preserved. PID/filename never authorizes a kill. Children
inherit closure, grant, lease slice and fence and cannot widen them.

Resource keys include process/role/host, RAM, target, cash, portfolio, player
activity, terminal, player interaction, CCT claim, root target, cloud slot,
DNET session, GO game and renderer budget. Home is excluded from productive
allocation; its OPS reserve is measured control/bootstrap peak plus one largest
observer replacement plus 20%, rounded to game RAM units. ROOT, ACTIVITY and
GO interaction effects are mutually exclusive; HACK and MULTI cannot share a
worker pool/target. Initial lease TTL is 5 s, renewal 1 s, and two missed
cadences pause new effects.

## Cash and capability boundary

One serialized arbiter ledger uses:

`available = max(0, observedCash - reserveFloor - liveUnspentReservations - unresolvedWorstCaseDebits)`.

Reservations bind maximum all-in cost (principal, fees, spread and bounded
expense), action, observation revision, constraints, expiry, grant, owner and
fence. Acceptance does not reserve; reservation does not authorize execution.
Buy, exit, CLOUD purchase and paid activity are separate operations. Unknown
exposure remains held until reality and causal evidence reconcile it. Manual
changes invalidate dependent intents; stopping preserves positions.

C01–C14 cover HACK, ROOT, CCT, ACTIVITY/AUG, DNET, CLOUD, STOCK observe,
STOCK policy/executor, GO, SHARE, MULTI and OPS. Their initial holds are no
allocator effect, no incidental purchase, no scarce retry, manual AUG boundary,
bounded DNET only, no CLOUD purchase, no stock capital call, simulation only,
exact capital authority plus A3, finite GO trial, separately approved SHARE,
money-only MULTI shadow and no broad killall.
