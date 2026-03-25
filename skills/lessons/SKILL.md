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

### Step 2b — Extract Quirk Markers

After writing the lesson, extract technical quirks and add structured HTML comment markers. For EACH technical failure, bug, or gotcha in the lesson, add:

```html
<!-- QUIRK: Short descriptive title -->
<!-- WHEN: Situation where this applies -->
<!-- WRONG: Code or approach that fails -->
<!-- RIGHT: Code or approach that works -->
<!-- WHY: One-sentence root cause -->
<!-- TAGS: comma-separated technology tags -->
```

Rules:
- Only extract TECHNICAL patterns (API quirks, code gotchas, platform constraints)
- Do NOT create quirks for reflections, confidence, impact, or hypotheses
- Place markers immediately after the relevant section
- Tags should describe the technology (e.g., google-apps-script, python, openshift, rust)
- Each marker should be self-contained

These markers enable automated quirk extraction via `generate-quirks.py`.

### Step 2c — Generate Quirk Tag Files

After writing the lesson with QUIRK markers, also generate the corresponding quirk tag files in `quirks/` using this format:

```markdown
# [Tag Name] -- Technical Quirks

triggers: [comma, separated, trigger, keywords]
updated: [YYYY-MM-DD]
count: [number of quirks]

---

### [Quirk title]
**When:** [situation]
**Wrong:** [what fails]
**Right:** [what works]
**Why:** [root cause]
*Source: [lesson-filename.md]*
```

Rules for quirk files:
- Group quirks by technology tag (one file per tag, e.g., `snowflake.md`, `python.md`)
- If a tag file already exists, append new quirks and update the count
- Triggers should be keywords that help someone find this quirk (tool names, error fragments, common terms)
- Update `_index.md` with the new/updated tag files

### Step 2d — Sanitize Personal Information

Before saving ANY lesson or quirk file, sanitize all personal information:

- Replace real usernames with generic placeholders (e.g., `YOUR_USER`)
- Replace real email addresses with `user@example.com` or `manager@example.com`
- Replace real account identifiers with `your-account-id`
- Replace resource IDs (Sheet IDs, project IDs, etc.) with `YOUR_SHEET_ID`, `YOUR_SCRIPT_ID`, etc.
- Replace OAuth client IDs with `YOUR_CLIENT_ID`
- Remove any API keys, tokens, bearer tokens, passwords, or secrets
- Remove real person names used as examples — use generic titles instead
- Keep product names, role patterns, and technical terms — only strip identifying info

**Test**: Run `grep -rn -i -E "(your_real_username|your_real_email|client_secret|api_key)" lessons/ quirks/` before committing. Output should be empty.

### Step 3 — Save and Share

Save the lesson file AND quirk tag files:

1. Save lesson to your lessons directory (e.g., `lessons/[slug].md`)
2. Save/update quirk tag files in `quirks/`
3. Update `quirks/_index.md`

Then commit and push:
```bash
git add lessons/[filename].md quirks/
git commit -m "Add lesson + quirks: [title]"
git push
```

If `generate-quirks.py` exists in the repo root and runs as a hook, it will auto-regenerate the quirk tag files from QUIRK markers. In that case, only commit the lesson file and let the hook handle quirks.

### Naming Convention

File names should be lowercase, kebab-case, and descriptive:
- `granite-tool-calling-quirks.md`
- `openshift-sandbox-no-internet.md`
- `internal-ssl-cert-errors.md`
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

---

## Direct Quirk Creation (without a lesson)

Quirks can also be created directly — without writing a full lesson first. This is for when the user says "create quirks" or "save these quirks" after a debugging session.

### When to create quirks directly

- After a debugging session where something non-obvious was discovered
- When the user says "create quirks", "save quirks", "document these gotchas"
- Proactively after hitting a technical pitfall during a build session
- When the conversation contains enough context to extract quirks without a full lesson

### Filing rules (critical — follow exactly)

1. **File by tool/technology** — name the file after the tech: `python.md`, `ollama.md`, `windows.md`. NEVER name it after the project (no `my-project-quirks.md`).

2. **Add to existing tag files first** — if `python.md` already exists, append your new quirk to it and increment the `count:` header. Only create a new tag file for a genuinely new technology.

3. **Update the index** — after adding/creating quirk files, update `_index.md`:
   - Increment `Total quirks:` and `Total tag files:` counts
   - Add new tag file rows to the Tag Files table

4. **One quirk = one pitfall** — each `###` block covers exactly one thing. Don't combine multiple issues into one block.

5. **Be specific** — include exact error messages, exact function names, exact commands. Someone should be able to ctrl+F their error and find the quirk.

### Where quirks live

Quirks are stored in a `quirks/` directory inside the user's training/enablement repo. Check the user's memory or ask them where their quirks repo lives. The directory contains:
- `_index.md` — summary index with counts and trigger keywords
- `{technology}.md` — one file per technology tag

### Common mistakes to avoid

- DO NOT save quirks to Claude Code auto-memory — they belong in the quirks repo
- DO NOT create a CLAUDE.md in the project repo for quirks — use the dedicated quirks directory
- DO NOT name quirk files after projects — name them after technologies
- DO NOT create a new tag file when an existing one covers the same tech — append instead
- DO commit and push quirks to the remote repo after creating them
