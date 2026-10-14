---
name: handle-review
description: Collects CodeRabbit, CI and Claude review feedback on a PR, recommends
  fix or skip for each, and applies only the approved fixes. Use when a PR has comments.
argument-hint: "[pr-number]"
---

# Handle review feedback on PR $ARGUMENTS

1. Gather everything:
   - `gh pr view $ARGUMENTS --comments`
   - `gh api repos/{owner}/{repo}/pulls/$ARGUMENTS/comments` (line comments)
   - `gh pr checks $ARGUMENTS` (CI status)
2. Verify each comment against the actual code before agreeing with it.
   Reviewers, including AI ones, are sometimes wrong or over-engineer.
3. Show a numbered table: reviewer, comment (short), your recommendation
   (fix / skip), one-line reason.
4. STOP and wait for me to choose.
5. Fix only what I approved. Run the rust-check skill.
6. For each skipped comment, draft a polite one-line reply; post replies only after
   I approve them.
7. Commit ("Address review feedback"), push, and comment `@coderabbitai review`.
