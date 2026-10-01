# Claude Skills

Small Claude Code skills I use every day. Copy what's useful and change it to fit how you work.

## Install

Copy a skill's folder into `~/.claude/skills/`. It then works in every project, git repo or not.

```bash
git clone https://github.com/seanmishra/claude-skills.git
cp -R claude-skills/handoff claude-skills/pickup ~/.claude/skills/
```

## Skills

### handoff and pickup

A pair for starting fresh sessions without losing the goal.

- `/handoff` writes a short note to `.scratch/handoff.md` for the next session: goal, done, next, in-flight context, pointers and suggested skills, plus the commit it was written at and any uncommitted files. It aims for about 60 lines. Before writing, it moves lasting decisions and gotchas to their real home (`CLAUDE.md`, docs, a skill's gotchas, or memory) after you approve one list, and puts open work that outlives the next session in `.planning/backlog.md`, or in your project's own tracker if it has one.
- `/pickup` reads the note in a new session, checks it against the project (commits since the recorded one, working-tree changes, the files it names), warns if it's over a week old, loads the suggested skills, and reports back. Once you say go, it renames the note to `handoff.prev.md`, so the same note can't be resumed twice and one backup stays around.

I run `/handoff` when I finish a session and `/pickup` to start the next one. The context window resets, and the goal carries over. Since each pickup consumes the note, it stays short, and anything meant to last ends up in the repo.

`/handoff` only runs when you type it. Claude can suggest it but won't trigger it on its own. Pass what the next session is for as an argument, like `/handoff build the export skill`, and the note focuses on that.

Keep `.scratch/` in `.gitignore`, since the note is temporary. Commit `.planning/`, since the backlog is meant to last.

If you already use a bigger planning system or workflow, keep it. These are a small default for when you don't have one.

## License

MIT
