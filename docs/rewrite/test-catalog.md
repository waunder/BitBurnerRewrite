# Rewrite test catalogue

Contract revision: B05/1. Cases are synthetic unless explicitly labelled
captured. Retain fixture digest, input revisions, expected/actual, event chain
and relevant API/process/file diff. Unauthorized effect, unowned kill,
wrong-target write, silent loss or unexplained duplicate is an immediate stop.

| Group | Independent oracle | Layers and gate |
| --- | --- | --- |
| AU01–03 authority | Delivery, override or proposal cannot infer authority; valid OPS scope only; forgery, expiry and revocation deny. | T0–T3, G2 |
| ID01–02 identity | Wrong/cloned registration, marker, epoch or session denies before target write; re-registration required. | T1–T4, B05-P |
| OB01–02 observations | Stale member, reordered sequence, skew or changed mutable input invalidates an action at final validation. | T1–T3 |
| OW01–04 ownership | One current fence; stale owner denied; PID reuse/foreign work preserved; no transfer before quiescence. | T1–T4, F06 |
| RE01–05 releases | Canonical closure succeeds; altered/missing/extra path, CAS conflict, torn chain, late resync and protected GC deny safely. | T0–T4, B05-P/F02 |
| CA01–03 cash | Shared reservations serialize; drift/manual change invalidates; unknown debit/position remains held; no exit without grant. | T0–T3, A3/C07/C09 |
| MN01–02 manual | Matching state without provenance, null state, manual activity/terminal use and failed restore preserve manual reality. | T1–T4 |
| EV01–04 events | Writer/ack failure, saturation/gap and unresolved compaction deny effects; duplicate export dedupes; only equivalent info coalesces. | T1–T4, B05-P/F03 |
| CT01 controls | Local/game parity; stale revision rejects; expiry restores precedence; pause dominates act request. | T1–T4 |
| TR01–02 transport | Pinned inactive delivery only; interrupted carrier/RPC/late response becomes bounded unknown or denial. | T3–T5 |
| SC01–02 scheduler | R1–R8 equations, allocation conservation, score variants and 0.79/0.80 guard are separate fixtures. | T1–T4, A4 |
| CP01–03 capability | CCT/DNET, GO/SHARE, AUG/ROOT/OPS failure paths remain bounded, manual or inactive as specified. | T0–T4 |
| MG01 migration | Legacy/rewrite remain independent; same-save observer has zero effect; handover reconciles reality first. | T4–T6 |

B05-P is limited to admission/clone, namespace/closure, an independent benign
diagnostic, same-save observer, A/B identity, CAS fault, event durability,
carrier-session interruption and scoped cleanup. It has a 60-minute limit, two
tiny releases, one active browser environment, no capability effects, and the
stop conditions in the documentation/test plan.

## A1 closure matrix

The following rows expand the grouped catalogue into the negative cases that
must be fixed before the named gate. Every fixture is synthetic unless marked
otherwise; an implementation test may split a comma-separated stimulus into
subcases but may not omit one. An `effect` below includes source activation and
owned lifecycle changes.

| A1 / test ID and stimulus | Fixture origin and independent expected result | Owner, layer/gate and case stop condition |
| --- | --- | --- |
| A1-01 AU11: delivered STOCK executor/no capital grant; override requests `act`; accepted proposal/no grant; old browser grant replayed on Steam; grant expires between acceptance/execution; lower-precedence control counters pause/revocation | Synthetic authority registry, desired state and call spy. Each denies durably before the call spy; no authority is inferred or broadened. | Control/authority owner; T0–T3, G2/F04/F06. Stop on any API call, grant mutation or effective value that weakens pause/revocation. |
| A1-02 ID11: wrong class/registration/marker/adapter; copied marker; unknown identity; old epoch; clone re-registration; reset between proposal/execution; stale session response | Synthetic envelope/admission fixtures; B05-P uses an externally registered disposable clone. Refuse before target write/start; clone/new epoch has inert copied records. | Identity/release owner; T1–T4, B05-P P01. Stop on any wrong-target write/start or acceptance of copied authority/lease/control. |
| A1-03 OB11: stale member in fresh composite; late older observation; clock skew; cash/price/fee/position change; CCT tries/fingerprint change; RAM/process change; manual/terminal change; reset epoch change | Synthetic multi-producer observation batches and final-call spy. Name precondition failure and make zero API calls or blind retries. | Observation/events owner; T1–T3, G2/F03/F06 and capability gate. Stop on stale promotion, cross-epoch acceptance, zero-fill or API call after invalidation. |
| A1-04 OW11: simultaneous lease request; expired/revoked owner spawn; PID reuse; partial drain; foreign/manual process; legacy relaunch; CCT/SHARE preemption; HACK/MULTI overlap; owner crash | Synthetic lease/process ledger; B05-P P04 observes a benign foreign legacy diagnostic only. Exactly one current fence; no transfer before two quiescence observations/release receipt; zero unowned kills. | Arbiter owner; T1–T4, B05-P P04–P06/F06/A2. Stop on dual current fence, unowned kill, stale spawn or transfer through ambiguity. |
| A1-05 RE11: same-size byte change; missing/extra/duplicate/traversal path; failed import/undeclared child; concurrent CAS; crash before/after pointer; reconnect while staging; old generation child after new delivery/fence revoke; mutable control survives delivery; protected GC | Synthetic closure/pointer/control fixtures; B05-P uses two tiny releases. Bad release remains inactive, predecessor unchanged; one successor only; old child keeps its own closure until fenced. | Release/transport owner; T1–T4, B05-P P02/P05/P06 and F02. Stop on mixed/active bad closure, second start, control overwrite or protected deletion. |
| A1-06 CA11: simultaneous STOCK/CLOUD/paid activity; price/fee above reserve; manual spend; manual/imported holding; sell without exit grant; stop with holding; partial/unknown order; unknown CLOUD name/slot; duplicate action; reset between reserve/execute | Synthetic cash ledger using the worked arithmetic in B05/1 §8 and call spies. Serialized reservations preserve floor and worst exposure; no automatic sell, compensation, duplicate or epoch reuse. | Cash/portfolio owner; T0–T3, G2/C07/C09/A3 (T4 capital case only if authorized). Stop on overspend, reservation double release, automatic liquidation or blind retry. |
| A1-07 MN11: manual activity during cooldown; matching but foreign activity; null/unavailable work; terminal use before/during backdoor; failed hop/install/restore; stale restart state; ROOT/ACTIVITY/GO concurrency | Synthetic activity/terminal provenance fixtures. Preserve manual/unknown reality; at most one composite interaction owner; show recovery rather than home reset. | Manual-interaction capability owner; T1–T4, C03/C05/C11. Stop on takeover without provenance/lease, hidden retry or terminal reset. |
| A1-08 EV11: logger unavailable/write failure/outbox full/sequence gap/schema mismatch; restart after accepted-before-call; crash after possible call-before-completion; compaction with unresolved attempt | Synthetic outbox/archive and call-spy fixtures; B05-P P07 covers writer/archive failure. Deny before effect when durability is absent; otherwise persist unknown and pin causal records. | Event/evidence owner; T1–T4, B05-P P07/F03/F06. Stop on effect without durable pre-record, false completion, blind retry or eviction of unresolved evidence. |
