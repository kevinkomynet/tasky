---
name: tdd-rust
description: Builds one GitHub issue in Rust with strict red-green-refactor TDD.
  Use when implementing any feature or bug fix in this repository.
argument-hint: "[issue-number]"
---

# Test-driven development for issue $ARGUMENTS

## 0. Understand
- `gh issue view $ARGUMENTS`, then read docs/PRD.md and docs/DESIGN.md.
- Create branch feature/$ARGUMENTS-<short-name> from an up-to-date main.
- Summarise in plain English what you'll build and list each acceptance criterion.

## 1. Red
- Write one test per acceptance criterion. Name tests like sentences:
  `adding_an_empty_task_is_rejected`.
- Logic goes in `#[cfg(test)] mod tests`; end-to-end behaviour goes in tests/
  using assert_cmd.
- Run `cargo test`. Show me the failures and confirm each fails for the RIGHT
  reason (missing feature, not a typo or compile error in the test).
- STOP. Wait for me to approve the tests before writing any feature code.

## 2. Green
- Write the minimum code that makes the tests pass. Nothing the issue didn't ask for.
- Run `cargo test` and show the result.

## 3. Refactor
- Improve names and structure without changing behaviour; keep tests green.
- Run the rust-check skill.

## 4. Teach
- Explain the new Rust concepts used (ownership, Result, traits...) in a few lines,
  pointing at real lines in this branch.
