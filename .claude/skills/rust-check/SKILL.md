---
name: rust-check
description: Runs the Rust quality gate (fmt, clippy, tests) and fixes problems.
  Use before every commit, and before saying any work is done or passing.
allowed-tools: Bash(cargo fmt *) Bash(cargo clippy *) Bash(cargo test *) Bash(cargo build *)
---

# Rust quality gate

Run these in order. Stop at the first failure, fix it, then start again from the top.

1. `cargo fmt --all`
2. `cargo clippy --all-targets -- -D warnings`
3. `cargo test`

Rules:
- Never silence a warning with `#[allow(...)]` unless I agree. Fix the cause.
- For each clippy warning you fix, give me one line: what it meant and why it matters.
- Never claim "done", "fixed" or "passing" without pasting the final lines of
  `cargo test` output from THIS run.

Report as a short table: check, result, notes.
