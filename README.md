# BitBurner Rewrite

This repository is the isolated home for the next BitBurner control and
monitoring system. It intentionally contains no copied legacy implementation
at initialization.

> **What this repository actually is.** A personal sandbox for learning to work
> with AI coding assistants, using the game Bitburner as the exercise. Every
> script here may be written through conversation with AI assistants, not by
> me. I have no meaningful coding background of my own that isn't 50 years out
> of date, and I make no claim to have progressed through the game on my own
> programming skill — this is a "vibe coding" log, not an example of
> hand-authored strategy code. If that's useful or interesting to you as a
> reference for AI-assisted development, great; just don't mistake it for my
> own engineering work.

The legacy system remains in the separate `BitBurner` repository and its
Steam save remains the protected live environment. Rewrite integration work
runs only against a separate browser save until a later, evidence-backed
promotion gate.

The initial work is planning, evidence inventory, and isolation validation;
implementation begins only after those gates are satisfied.

Only source, reviewed documentation, reproducible fixtures, and deliberately
sanitized evidence belong here. Never commit a Bitburner save, credentials,
private telemetry, live stock/accounting state, local endpoint details, or
Steam-targeted configuration.
