---
name: handoff
description: Save the current session to .scratch/handoff.md so a later session can pick it up.
argument-hint: "What will the next session be used for?"
disable-model-invocation: true
---

A handoff is a short note from this session to the next one. It holds only session-scoped state and lives until `/pickup` consumes it. Lasting facts move to their permanent homes, and open work that outlives the next session goes to the backlog.

1. **Check for an unpicked handoff.** If `.scratch/handoff.md` exists, nobody picked it up. Read it and ask the user whether to merge it into this one or overwrite it. `.scratch/handoff.prev.md` is the consumed copy from the last `/pickup`; leave it alone.
   Done when: the user has chosen, or there was no file.

2. **Promote lasting facts.** Go through the session (and any handoff you are merging) for decisions, conventions and gotchas that will still hold after the next session. Pick each one's home: the project's `CLAUDE.md` or docs, the Gotchas of the skill it concerns, or auto-memory for facts about the user or how they work. Show the user one list of `fact → destination` and apply it after one approval, with any edits they make. Skip facts already written down there.
   Done when: every lasting fact is either in its home or dropped by the user.

3. **Update the backlog.** Open items the next session won't finish go to the project's own tracker if it has one (issues, a TODO file), otherwise to `.planning/backlog.md`, which is committed. Each entry is a few lines: what, why, and what blocks it. A plan too detailed for a few lines gets its own file in `.planning/backlog/<slug>.md`, and its entry points to it. Remove entries this session finished, and delete their plan files.
   Done when: every open item outside the next session's scope is in the backlog, and nothing finished remains there.

4. **Write `.scratch/handoff.md`.** Aim for about 60 lines. Going over means something belongs in step 2 or 3. Cover:
   - **Written**: date, `git rev-parse --short HEAD`, and the uncommitted files from `git status --short`, with what each change is.
   - **Goal**: what the next session works toward and which files it concerns.
   - **Done**: what this session finished, with paths or commits.
   - **Next**: the open steps for the next session, in order, each specific enough to act on.
   - **Context**: in-flight state the files alone don't show, such as half-made choices, questions waiting on the user, or why something was paused.
   - **Pointers**: backlog entries and docs the next session should read.
   - **Suggested skills**: skills the next session should load.

   Point to existing material by path or URL; summarize only what lives in the conversation. Redact API keys, passwords and personal information. If the user passed arguments, treat them as the next session's focus and shape Goal and Next around it.
   Done when: the file is saved and under about 60 lines, or the user accepted the overage.

5. **Report.** Tell the user what was promoted, what changed in the backlog, and that `/pickup` resumes from the handoff.

## Gotchas

- `.scratch/` is gitignored, so the handoff exists on one machine only. Everything that must survive goes through steps 2 and 3.
- Commit backlog and doc changes the way the project commits other work; leave the handoff itself out of git.
