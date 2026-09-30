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

- `/handoff` saves the session to `.scratch/handoff.md` in five sections: goal, done, next, decisions and suggested skills. It points to files and commits by path and summarizes only what lives in the conversation. If a note already exists, it carries the unfinished steps forward.
- `/pickup` reads that note in a new session, checks it against the project (the files it names, plus `git log --oneline -10`), loads the suggested skills, and reports back before doing any work.

I run `/handoff` when I finish a task and `/pickup` to start the next one. The context window resets, and the overall goal carries over.

`/handoff` only runs when you type it. Claude can suggest it but won't trigger it on its own. Pass what the next session is for as an argument, like `/handoff build the export skill`, and the note focuses on that.

Whether `.scratch/` goes in `.gitignore` is up to you. The skills work either way. I keep the note out of commits because it's a temporary scratch file.

If you already use a bigger planning system or workflow, keep it. These are a small default for when you don't have one.

## License

MIT
