# Rewrite operator guide (inactive skeleton)

No rewrite control surface is implemented. This document does not instruct an
operator to start or stop a game process.

When implemented, the surface shows environment/epoch/admission, active
release/generation, desired-state layers, grants, leases, reservations,
observed conformity, event health and capability ROI. Its controls are inspect,
propose, typed preference/override, pause, drain, owned stop, release request
and rollback request. Each change is revisioned and shows actor, reason and
expiry.

Pause denies new effects. Drain permits only already-started work to its
deadline. Owned stop applies only to proven owned identities and does not sell
positions, cancel manual activity, undo a contract attempt or reset progress.
Unknown environment, authority, evidence or ownership means observe/propose
only and needs operator resolution.
