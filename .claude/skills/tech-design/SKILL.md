---
name: tech-design
description: Writes or updates docs/DESIGN.md, a short technical design for this Rust CLI.
  Use when planning architecture, choosing crates, or before building a milestone.
---

# Technical design (Rust)

Read docs/PRD.md and the current src/ first. The user is a Rust beginner:
explain every choice in one plain-English sentence.

docs/DESIGN.md must cover, briefly:
1. Crates: each one, why it beats the alternative, and its job. Prefer well-known
   crates (clap, serde, serde_json, anyhow or thiserror, assert_cmd for tests).
2. Data model: the main structs and enums, with field names and types.
3. Module layout: one line per file under src/.
4. Storage: file location, format, behaviour when the file is missing or corrupt.
5. Errors: what the user sees for each failure; exit codes.
6. Testing: which logic gets unit tests, which behaviour gets integration tests
   in tests/ that run the real binary.
7. Risks and open questions.

Keep it under two pages. No code beyond type signatures.
If the PRD and the design disagree, stop and ask which one should change.
