---
name: open-pr
description: Commits, pushes and opens a pull request for the current feature branch.
  Use when a feature is finished and the quality gate passes.
disable-model-invocation: true
allowed-tools: Bash(git status *) Bash(git diff *) Bash(git log *)
---

# Open a pull request

1. Refuse if the current branch is main. Tell me and stop.
2. Run the rust-check skill. Stop if anything fails.
3. Show me `git status` and a summary of the diff. Ask before committing.
4. Commit with a short imperative message ("Add task list command").
5. `git push -u origin HEAD`
6. `gh pr create` with:
   - Title: same style as the commit message
   - Body sections: What changed / Why (link the issue) / How to test manually
     (exact commands) / Notes for reviewers
   - The line "Closes #<issue-number>"
7. Comment `@coderabbitai review` on the new PR with `gh pr comment`.
8. Give me the PR link.
