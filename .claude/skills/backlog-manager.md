---
name: backlog-manager
description: Triages GitHub issues and updates backlog state
---

# Backlog Manager Skill

When executing this skill:

1. **Inspect Issues:** Read all open issues in the current repository using the GitHub CLI (`gh issue list`) or API.
2. **Triage & Assess:**
   - Review each issue for status, context, and proper labels.
   - For unlabelled issues, apply managed labels and add an "Agent Assessment" comment.
   - Check if any open issues have linked merged PRs; close them with linked evidence.
   - Create evidence-backed issues if missing bugs or gaps are identified.
3. **Project Board Actions:**
   - Formulate proposed changes for the target project board.
   - **Do NOT execute project board mutations directly.** List them as proposed actions in the report instead.
4. **Execution Mode Handling:**
   - **dry-run mode:** Inspect and triage only. Make zero actual mutations (no labels, comments, or closes). Report proposed changes only.
   - **apply mode:** Perform allowed mutations (labels, comments, closing issues with merged PR evidence, creating new issues).
5. **Final Output:**
   End with a compact summary containing:
   - Mode
   - Issues inspected
   - Issues triaged
   - Labels/comments created
   - Proposed project-board changes
   - Blockers
