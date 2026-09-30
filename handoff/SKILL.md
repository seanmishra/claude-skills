---
name: handoff
description: Save the current session to .scratch/handoff.md so a later session can pick it up.
argument-hint: "What will the next session be used for?"
disable-model-invocation: true
---

Write a handoff document that lets a fresh session continue this work, and save it to `.scratch/handoff.md` in the project root.

If a handoff file already exists, read it before writing. Carry its unfinished next steps, still-relevant decisions and useful gotchas into the new document, and drop anything this session finished or made obsolete. Then replace the file with the merged version.

Cover:

- **Goal**: what we are working toward and which files or folders it concerns.
- **Done**: what was finished this session, with file paths.
- **Next**: the open steps, in order, each specific enough to act on.
- **Decisions**: choices made and the reason for each, especially ones the files alone would not reveal.
- **Suggested skills**: skills the next session should load.

Point to existing material (specs, docs, issues, commits) by path or URL. Summarize only what lives in the conversation.

Redact API keys, passwords and personal information.

If the user passed arguments, treat them as the focus of the next session and tailor the document to it.

Finish by telling the user the file is saved and that `/pickup` resumes from it.
