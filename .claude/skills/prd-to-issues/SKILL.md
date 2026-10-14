---
name: prd-to-issues
description: Turns the user stories in docs/PRD.md into GitHub Issues with labels.
  Use when the PRD is approved and the backlog needs creating or updating.
disable-model-invocation: true
allowed-tools: Bash(gh issue list *) Bash(gh label list *)
---

# PRD to GitHub Issues

1. Read docs/PRD.md. List every user story (US-n) and its milestone.
2. Run `gh issue list --state all --limit 200` so you never create a duplicate.
   Skip any story whose ID already appears in an issue title.
3. Make sure labels v0.1, v0.2 and v0.3 exist (`gh label list`; create missing
   ones with `gh label create`).
4. For each new story, show me the draft title and body first. After I approve,
   run `gh issue create` with:
   - Title: "US-n: <story name>"
   - Body: the user story, then acceptance criteria as a "- [ ]" checklist,
     then "Source: docs/PRD.md"
   - Label: its milestone
5. Finish with a table: issue number, title, label.
