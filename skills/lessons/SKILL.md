# Lessons

## Overview

Captures hard-won knowledge into structured, reusable lesson files. When someone discovers a quirk, workaround, or "I wish someone had told me this" moment, this skill turns it into a lesson that others can learn from.

**Keywords**: lesson, create a lesson, generate a lesson, document this, write this up, what I learned, gotcha, quirk, workaround, TIL

## How It Works

### Step 1 — Gather the Facts

If the user hasn't provided details, ask these questions (skip any they've already answered):

1. **What happened?** — What were you trying to do?
2. **What went wrong?** (or what was unexpected)
3. **What did you discover?** — The fix, workaround, or insight
4. **What should someone do instead?** — The recommended approach

If the conversation already contains this context (e.g., they just debugged something with you), extract it automatically — don't make them repeat themselves.

### Step 2 — Generate the Lesson

Write a markdown file using this exact format:

```markdown
# [Title — clear, searchable, specific]

**Discovered**: [Month Year]
**Context**: [Tool/platform/language this applies to]

## The Problem

[1-2 paragraphs. What were you trying to do? What happened instead?
Include the exact error message or unexpected behavior if applicable.]

## What You'll See

[Show the actual output, error, or behavior. Code blocks with real examples.
This helps people recognize "oh, that's what's happening to me too."]

## The Fix

[Step-by-step solution. Code examples. Be specific enough that someone
can copy-paste and solve their problem.]

## Why This Happens

[Optional but valuable. The root cause — helps people understand,
not just follow instructions.]

## Recommendation

[One sentence: what to do going forward. The TL;DR.]
```

### Step 3 — Save and Share

Save the lesson file to the current directory as `lessons/[slug].md` where the slug is a kebab-case version of the title.

Then ask the user:

> "Lesson saved to `lessons/[filename].md`. Want me to commit it and create a merge request to the team's training repo?"

If yes:
1. `git add lessons/[filename].md`
2. `git commit -m "Add lesson: [title]"`
3. `git push`
4. Create an MR if they have a fork of a shared repo configured

### Naming Convention

File names should be lowercase, kebab-case, and descriptive:
- `granite-tool-calling-quirks.md`
- `openshift-sandbox-no-internet.md`
- `red-hat-internal-ssl-certs.md`
- `python-async-windows-event-loop.md`

NOT: `lesson1.md`, `notes.md`, `fix.md`

### Auto-Detection

If the user just finished debugging something with Claude and says any of these, trigger this skill:
- "create a lesson about this"
- "write this up as a lesson"
- "document this for the team"
- "generate a lesson"
- "save this as a lesson"
- "TIL" / "today I learned"
- "someone else should know about this"
- "I don't want anyone else to hit this"

Pull the problem, discovery, and fix from the conversation history — don't ask questions they've already answered.

## Trigger Phrases

- "create a lesson"
- "generate a lesson"
- "write a lesson about"
- "document this"
- "save this as a lesson"
- "write this up"
- "TIL"
- "today I learned"

## Tone

- Practical: someone is reading this because they're stuck. Get to the fix fast.
- Specific: exact error messages, exact commands, exact versions.
- Honest: "We tried X and it didn't work" is valuable. Don't hide the failures.
- Generous: write it for the person who will Google this at 11pm.
