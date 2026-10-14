---
name: fix-ci
description: Diagnoses and fixes a failing GitHub Actions run on the current branch.
  Use when a PR check is red or the user says CI failed.
allowed-tools: Bash(gh run list *) Bash(gh run view *) Bash(gh pr checks *)
---

# Fix failing CI

1. `gh pr checks` to find the failing check, then
   `gh run view <run-id> --log-failed` to read only the failing steps.
2. Explain the failure in plain English in two sentences.
3. Reproduce it locally with the same command (cargo fmt --check, clippy or test).
   If it passes locally but fails in CI, say so and compare toolchain versions.
4. Find the root cause before changing anything. No guess-and-retry loops.
5. Fix it, run the rust-check skill, commit ("Fix CI: <cause>") and push.
6. Watch the new run with `gh run watch` and report the result.
