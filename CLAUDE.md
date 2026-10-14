# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project state

`tasky` is a freshly scaffolded Rust binary crate (`cargo new` output): `src/main.rs` is still the "Hello, world!" stub, there are no dependencies, and `docs/` is empty. There is no established architecture yet — update this file as modules and conventions take shape.

- Rust edition **2024** (requires Rust 1.85+).
- Single binary crate; entry point is `src/main.rs`.

## Commands

```sh
cargo build                 # build
cargo run -- <args>         # run the binary
cargo test                  # run all tests
cargo test <name_substring> # run a single test (or tests matching a name)
cargo test <name> -- --nocapture  # show println! output from a test
cargo clippy --all-targets -- -D warnings  # lint (warnings fail)
cargo fmt                   # format
```

## How we work

- The user is the product manager and a Rust beginner. Explain Rust concepts in plain English when you introduce them.
- Requirements live in `docs/PRD.md` and design in `docs/DESIGN.md`. Read them before starting any feature.
- Every piece of work starts from a GitHub Issue. Use `gh` to read issues (e.g. `gh issue view <number>`).
- Never commit directly to `main`. Create a branch named `feature/<issue-number>-<short-name>` or `docs/<short-name>`.
- Use test-driven development: write failing tests first, show them failing, then write the minimum code to pass, then refactor.
- Before every commit, run these; all must pass:
  ```sh
  cargo fmt
  cargo clippy --all-targets -- -D warnings
  cargo test
  ```
- Keep pull requests small: one issue per PR. Put `Closes #<issue-number>` in the PR description.
- Commit messages: short imperative summary, e.g. "Add task list command".
- Never use `--force`, `reset --hard`, or delete files outside this project without asking first.
