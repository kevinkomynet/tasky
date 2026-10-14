---
name: review-pr
description: Independent senior Rust review of the current branch against its issue and
  the design. Use after a PR is opened, ideally in a fresh session (/clear first).
argument-hint: "[pr-number]"
---

# Senior Rust review of PR $ARGUMENTS

You did not write this code. Review it as a sceptical senior engineer.

1. `gh pr view $ARGUMENTS` and `gh pr diff $ARGUMENTS`.
2. Find the linked issue ("Closes #n") and read its acceptance criteria.
3. Read docs/DESIGN.md.

Check, in this order:
1. Correctness: does each acceptance criterion have a passing test that really
   proves it? Any criterion untested?
2. Bugs: panics (`unwrap`, indexing), wrong error handling, data loss on save.
3. Design drift: anything that contradicts docs/DESIGN.md or adds unrequested scope.
4. Readability: names, function length, comments that lie.
5. Learning: one or two things a Rust beginner should take from this code.

Output a numbered list grouped by severity: Must fix / Should fix / Nit.
Each item: file:line, problem, suggested fix. Don't edit any files.
Then ask whether to post the review with `gh pr comment $ARGUMENTS`.
