# Rewrite release and event contract

Contract revision: B05/1. Path/runtime mechanisms are hypotheses until the
disposable-browser proof; failed proof leaves delivery and activation inactive.

## Immutable release and activation

A release is a SHA-256 canonical UTF-8 descriptor of compatible schemas,
entrypoints, bootstrap compatibility and sorted `{path, byteLength, sha256,
role}` closure entries. Paths are relative POSIX with no traversal, duplicates,
case aliases or undeclared fields. Commit/URL/time are provenance outside the
descriptor. Closure includes imports, dynamic children, templates and declared
helpers; runtime code resolves only within that closure. Mutable controls and
accounting never enter it.

Stage a new inactive release, inventory/read every byte and issue an append-only
verified-release receipt containing envelope, release ID, descriptor digest,
per-file results, verifier/bootstrap identity and evidence. Missing, extra,
duplicate or mixed bytes deny activation. Release, state, event, controls and
bootstrap paths are distinct; legacy roots are never overwritten.

The arbiter alone updates an append-only active-generation CAS chain. A pointer
binds predecessor revision/digest, verified receipt, release, generation,
schemas, desired revision, root owner token, action and
`pending|observed-active|unknown` state. Concurrent/torn successors or a lost
acknowledgement are conflict/unknown, not a second start. Running A remains A
and can launch only A-closure children while fenced. Rollback uses verified
prior bytes under a new generation and fresh authority. Active, draining,
recovery and unresolved-attempt dependencies cannot be garbage-collected.

## Canonical events and durability

Events contain `producerBootNonce:sequence`, producer/release/generation/process
identity, envelope, occurrence/receipt time, level/kind, correlation/action/
attempt, human message, predicate inputs, schema and payload digest. Ordering
is monotonic only per producer. Export is at-least-once, deduplicates equal
event ID/digest and acknowledges only a contiguous verified prefix; gaps block
dependent effects.

Capacity: 16 KiB event, 256 KiB segment, 8 MiB game buffer; warn at 75%, pause
admission at 90%, never overwrite at 100%. Block new effects below 512 MiB
external free space or without verified archive commit. Resolved records retain
30 days; unresolved attempts and causal grants/fences/inputs remain pinned.

Every game API effect, scarce attempt, paid action, ownership transfer,
activation and owned lifecycle change is evidence-required. Before it, accepted
intent with authority/input/lease/reservation refs and unique attempt, then
`started`, must have game readback and acknowledged external archive commit
surviving writer restart. Logger failure is never authority to continue.
Diagnostic rendering is best effort. All projections derive from these events;
only equivalent informational records coalesce, never decisions, changed inputs,
warnings or errors.
