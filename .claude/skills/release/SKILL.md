---
name: release
description: Prepares and publishes a tagged GitHub release for a milestone.
  Use only when the user asks to release a version.
argument-hint: "[version e.g. 0.1.0]"
disable-model-invocation: true
---

# Release v$ARGUMENTS

1. Confirm every issue labelled with this milestone is closed:
   `gh issue list --label v<major.minor> --state open`. If any are open, stop.
2. From an up-to-date main, create branch release/v$ARGUMENTS.
3. Set `version = "$ARGUMENTS"` in Cargo.toml; run `cargo build` to refresh Cargo.lock.
4. Update README.md: what tasky does, install (`cargo install --path .`), every command
   with an example.
5. Run the rust-check skill, then use the open-pr skill.
6. AFTER I merge the PR: switch to main, pull, then
   `gh release create v$ARGUMENTS --generate-notes --title "tasky v$ARGUMENTS"`.
7. Give me the release link.
