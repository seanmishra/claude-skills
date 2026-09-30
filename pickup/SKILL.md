---
name: pickup
description: Resume work from .scratch/handoff.md. Use when the user says pick up, carry on, or continue from last session.
---

1. Read `.scratch/handoff.md` in the project root. If it is missing, tell the user and stop.
2. Check the handoff against the project: confirm the files and folders it names are where it says, and in a git repo run `git log --oneline -10` for commits made since. Note anything that moved or changed since it was written.
3. Load the skills listed under suggested skills.
4. Report back in a few lines: the goal, what is done, the first next step, and any drift found in step 2. Wait for the user's go-ahead before starting the work.
