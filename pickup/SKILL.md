---
name: pickup
description: Resume work from .scratch/handoff.md, or from the backlog when there is none. Use when the user says pick up, carry on, or continue from last session.
---

1. **Read the handoff.** Read `.scratch/handoff.md` in the project root. If it is missing, the last session ended at a clean point: read the backlog (the project's own tracker, or `.planning/backlog.md`), offer its top few entries as a starting point, and wait for the user to pick. With no backlog either, tell the user there is nothing to resume and stop. Mention `.scratch/handoff.prev.md` only if the user asks about the last handoff. Steps 2 to 5 apply only when a handoff exists.
   Done when: the file is read, or the user has the backlog's top entries, or knows there is nothing to resume.

2. **Check for drift.** Note the handoff's age from its Written date and flag it if it is more than 7 days old. In a git repo, run `git log --oneline <sha>..HEAD` with the sha it recorded, and compare `git status --short` with the uncommitted files it listed. Confirm the files and folders it names are where it says.
   Done when: every commit since the sha, every working-tree difference and every missing path is noted.

3. **Load the skills** listed under Suggested skills, and read the backlog entries and docs under Pointers.

4. **Report and wait.** In a few lines: the goal, what is done, the first next step, and any drift from step 2. If the handoff is stale, ask whether it still applies. Wait for the user's go-ahead.

5. **Consume the handoff.** On the go-ahead, rename `.scratch/handoff.md` to `.scratch/handoff.prev.md`, replacing any older one, so the next `/pickup` can't resume it twice. The session now carries its contents, and `/handoff` writes a fresh one at the end.
   Done when: `.scratch/handoff.md` no longer exists.
