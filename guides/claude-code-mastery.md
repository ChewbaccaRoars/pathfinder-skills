# Claude Code Mastery -- Self-Guided Learning Guide

**From first command to power user. Everything you need to know about Claude Code, organized by skill level.**

| Level | Who it's for | Time |
|:------|:-------------|:-----|
| Level 1: Getting Started | Never used Claude Code before | 15 min |
| Level 2: Working Effectively | Comfortable with basics, want to go faster | 20 min |
| Level 3: Power User | Ready to customize and automate | 25 min |
| Level 4: Pro Tips & Tricks | Want every edge you can get | 15 min |

---

## Level 1: Getting Started (Beginner)

### What is Claude Code?

Claude Code is a command-line tool that lets you work with an AI assistant directly inside your terminal. Unlike browser-based chatbots (ChatGPT, Gemini), Claude Code has **tools** -- it can read your files, run shell commands, search your codebase, make edits, and use git. It doesn't just talk about code; it works with your actual project files on your machine.

**CLI vs. Chat -- when to use which:**
- Use **Claude Code** (CLI) when you're working on a project with files, code, configs, or anything on your local machine.
- Use **Claude.ai** (browser chat) for general questions, brainstorming, or when you don't need file access.

**How it differs from ChatGPT/Gemini:** Those tools can only read what you paste into them. Claude Code can navigate your entire project, read any file, run tests, commit to git, and make changes across multiple files -- all from natural language instructions.

### Your First 5 Minutes

**Opening Claude Code:**
```bash
claude
```
That's it. Run `claude` in your terminal from any project directory.

**Your first prompt -- explore the directory:**
```
What files are in this directory?
```
Claude uses its tools to list your files and gives you a summary. Try it now.

**Read a file -- just ask:**
```
Read package.json
```
or
```
Show me the config file
```
Claude finds and reads the file, then explains what's in it if you ask.

**Make a change:**
```
Add a comment to the top of main.py that says "Entry point for the application"
```
Claude will show you the proposed edit and ask for permission before writing.

**The permission model:** Claude always asks before modifying files, running commands, or doing anything destructive. This is by design -- you stay in control. You'll see a prompt asking you to approve, and you can say yes or no.

### Essential Commands

These are built-in slash commands you can type at any time:

| Command | What it does |
|:--------|:-------------|
| `/help` | Show help and available commands |
| `/clear` | Clear the conversation and start fresh |
| `/compact` | Compress context when the conversation gets long |
| `/cost` | Show token usage and cost for the session |
| `/model` | Switch between models (Opus, Sonnet, Haiku) |
| `/config` | Open settings |
| `/hooks` | View and manage automation hooks |
| `/status` | Show current status |
| `/memory` | View auto-memory (persistent notes) |
| `! command` | Run a shell command directly (e.g., `! git status`) |

**Try it now:** Type `/cost` to see how much your current session has used.

### The Permission System

Claude Code asks permission before it acts. Here's what you'll see:

- **"Allow once"** -- approve this single action
- **"Allow for session"** -- approve this type of action for the rest of the session
- **Permission rules** -- pre-approve categories of actions in your settings

You can pre-allow safe tools in your settings file so Claude doesn't ask every time:

```json
{
  "permissions": {
    "allow": [
      "Bash(git:*)",
      "Read",
      "Glob",
      "Grep"
    ]
  }
}
```

This tells Claude: "You can always read files, search, and run git commands without asking."

**The key principle:** Claude will never silently modify your files or run dangerous commands. You always get a say.

---

## Level 2: Working Effectively (Intermediate)

### Talking to Claude Code

**Be specific.** The more context you give, the better the result.

| Instead of this | Say this |
|:----------------|:---------|
| "Something is wrong" | "The login endpoint returns a 403 -- check the auth middleware in `src/auth.js`" |
| "Fix this" | "Fix the TypeError on line 42 of `utils.py` -- it's getting `None` when it expects a list" |
| "Make it better" | "Refactor `processOrder()` to handle the case where `items` is an empty array" |

**Give context up front:**
```
This is a React app using TypeScript and Tailwind. The API is in src/api/.
Add a dark mode toggle to the navbar component.
```

**Multi-step instructions work.** Claude remembers the entire conversation, so you can build on previous steps:
```
1. Read the database schema
2. Create a new migration that adds an "archived" column to the users table
3. Update the User model to include the new field
4. Write a test for the archive functionality
```

**When to start a new session:** Start fresh when you're switching to a completely different topic. If context from the old topic is cluttering the conversation, `/clear` or start a new `claude` session.

### File Operations

**Reading:** Claude reads files before editing them (and you should ask it to). This prevents blind edits.
```
Read src/config.ts and explain what each setting does
```

**Editing:** Claude uses two tools for changes:
- **Edit** -- surgical changes to specific lines (preferred for modifications)
- **Write** -- creates new files or complete rewrites

**Searching:** Two search tools cover different needs:
- **Glob** -- find files by name pattern: "find all `.test.ts` files"
- **Grep** -- find content inside files: "find everywhere we import the Logger class"

**Pro tip:** Always ask Claude to read a file before changing it. This avoids mistakes from working with stale or assumed content.

### Git Integration

Claude Code has full git integration. You can work with version control using natural language.

```
Commit this with a good message
```

```
Create a new branch called feature/dark-mode and commit these changes
```

```
What changed since yesterday?
```

```
Create a PR for these changes with a summary of what I built
```

```
Show me the diff for the last 3 commits
```

**Pro tip:** Claude automatically adds `Co-Authored-By` trailers to commits, so your team can see which commits involved AI assistance.

### Using Agents (Subagents)

Agents are separate Claude instances that run in parallel, each handling a different task.

**When to use agents:**
```
Use agents to review all 5 files in the api/ directory for security issues
```

```
Use agents to fix the lint errors in these 3 files simultaneously
```

**How it works:** Adding "use agents" to your prompt tells Claude to spin up parallel workers. Each agent gets its own context and works independently, then results are combined.

**Agent types:**
- **General-purpose** -- handles any task you describe
- **Explore** -- investigates a question across many files
- **Plan** -- creates a multi-step plan before executing

**Background agents:** You can fire off work and get notified when it's done -- useful for longer tasks like full codebase reviews.

**Pro tip:** Agent isolation means they can safely edit different files in parallel without conflicts. For edits to the same file, Claude uses git worktrees to prevent collisions.

---

## Level 3: Power User (Advanced)

### Custom Skills (Slash Commands)

Skills are reusable prompts that extend Claude's capabilities. They live as markdown files and teach Claude new behaviors.

**Where they live:**
- `~/.claude/skills/` -- your personal skills (available everywhere)
- `.claude/skills/` -- project-level skills (shared with your team via git)

**The SKILL.md format:**

```markdown
---
name: my-skill
description: What this skill does
---
# My Skill

## Behavior

When this skill is invoked, Claude should:
1. Do this first thing
2. Then do this
3. Format the output like this
```

**Installing community skills** (like the Pathfinder Skills collection):
```bash
# Install as a plugin
/plugin install ChewbaccaRoars/pathfinder-skills

# Or copy individual skills manually
mkdir -p ~/.claude/skills/my-skill
cp SKILL.md ~/.claude/skills/my-skill/SKILL.md
```

**Creating your own skill:** Think of a task you repeat often. Write the instructions as a SKILL.md file, save it to `~/.claude/skills/your-skill-name/SKILL.md`, and Claude picks it up automatically.

### Hooks -- Automate Everything

Hooks are shell commands that run automatically at specific points in Claude's lifecycle. They turn Claude Code into an automation platform.

**Hook events:**

| Event | When it fires |
|:------|:-------------|
| `PreToolUse` | Before Claude uses a tool (can block or modify) |
| `PostToolUse` | After Claude uses a tool (react to changes) |
| `Stop` | When Claude finishes responding (cleanup, commit, notify) |
| `SessionStart` | When a session begins (setup, welcome) |
| `PreCompact` | Before context compression |
| `PostCompact` | After context compression |

**Example: Auto-format code after every edit**

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "prettier --write \"$FILE_PATH\" 2>/dev/null || true",
            "timeout": 10,
            "statusMessage": "Formatting code..."
          }
        ]
      }
    ]
  }
}
```

**Example: Run tests after code changes**

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "npm test --silent 2>/dev/null || true",
            "timeout": 30,
            "statusMessage": "Running tests..."
          }
        ]
      }
    ]
  }
}
```

**Example: Auto-commit work when the session ends**

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "cd /path/to/project && git diff --quiet && exit 0; git add -A && git commit -m 'Auto-save from Claude session' || true",
            "timeout": 30,
            "statusMessage": "Saving work..."
          }
        ]
      }
    ]
  }
}
```

**Example: Regenerate derived files when source changes**

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "python3 generate-quirks.py 2>/dev/null || true",
            "timeout": 30,
            "statusMessage": "Regenerating quirk files..."
          }
        ]
      }
    ]
  }
}
```

**Pro tip:** Hooks + Skills = automation pipelines. A skill defines *what* Claude does; a hook defines *what happens automatically* after Claude acts.

### CLAUDE.md -- Project Instructions

CLAUDE.md is a markdown file that Claude reads at the start of every conversation. It's your way of giving Claude persistent instructions.

**Where to put it:**
- **Project root** (`./CLAUDE.md`) -- instructions for this project
- **Home directory** (`~/CLAUDE.md`) -- global instructions for all projects

**What to include:**
- Coding style and conventions: "Use single quotes, 2-space indent, no semicolons"
- Project-specific rules: "Always run `make lint` before committing"
- Common mistakes: "The database password env var is `DB_PASS`, not `DB_PASSWORD`"
- Architecture notes: "The API lives in `src/api/`, the frontend is in `src/web/`"

**Example:**

```markdown
# Project Instructions

## Style
- TypeScript with strict mode
- Use functional components, not class components
- All API responses use the `ApiResponse<T>` wrapper type

## Rules
- Never commit directly to main -- always use feature branches
- Run `npm test` before every commit
- All new endpoints need integration tests

## Gotchas
- The staging database has a 5-second timeout -- use connection pooling
- The `user.email` field is optional in v1 of the API -- always null-check it
```

**Pro tip:** Put your team's known gotchas in CLAUDE.md so Claude avoids them automatically. Every team member benefits.

### Auto-Memory

Auto-memory lets Claude save persistent notes that survive across sessions.

**Where it lives:** `~/.claude/projects/<project>/memory/`

**What to save:**
- Project decisions: "We chose PostgreSQL over MongoDB because..."
- User preferences: "I prefer functional style over classes"
- Architecture notes: "The auth service is a separate microservice at port 3001"
- Learned gotchas: "The CI pipeline requires Node 18, not 20"

**What NOT to save:** Temporary state, in-progress work, things that change frequently.

**How to use it:**
```
Remember that we use bun instead of npm for this project
```
Claude saves this to auto-memory and applies it in every future session.

```
/memory
```
View everything Claude has saved.

```
Stop remembering that we use yarn -- we switched to bun
```
Claude updates the memory.

### Settings Deep Dive

Claude Code has three layers of settings, each with a different scope:

| File | Scope | Committed to git? |
|:-----|:------|:-------------------|
| `~/.claude/settings.json` | All projects (global) | No |
| `.claude/settings.json` | This project (shared) | Yes |
| `.claude/settings.local.json` | This project (personal) | No (gitignored) |

**Key settings you can configure:**
- `model` -- default model (e.g., `"claude-sonnet-4-20250514"`)
- `permissions` -- pre-approved tools and commands
- `hooks` -- automation hooks (see Hooks section)

Settings cascade: project settings override global, local overrides project.

---

## Level 4: Pro Tips & Tricks

### The Pathfinder Skills System

Pathfinder is a collection of 19 skills designed for non-technical builders -- people who want to build automations, apps, and agents without a traditional developer background.

| Command | What it activates |
|:--------|:-----------------|
| `/learn` | Plain-English explanations + courage mode + discovery of unknown unknowns |
| `/build` | Find what to automate, form a hypothesis, build a rough v1 fast, connect APIs, level up to agents |
| `/reflect` | Journal learnings, track confidence, measure impact |
| `/share` | Create presentations, how-to guides, workshop plans, teach others |
| `/pathfinder` | See all options or let the router figure out what you need |

Just say `/pathfinder` and it routes you to the right tool based on what you say.

**Install Pathfinder:**
```bash
/plugin install ChewbaccaRoars/pathfinder-skills
```

### The Quirk Extraction System

When you discover a technical gotcha, capture it as a lesson so future sessions (and teammates) avoid the same mistake.

**The workflow:**
1. You discover a bug, quirk, or workaround during a session
2. Say `"create a lesson"` -- Claude writes a structured lesson file
3. Claude adds `<!-- QUIRK: ... -->` markers for each technical pattern
4. A generator script (`generate-quirks.py`) extracts markers into organized quirk files
5. Claude reads quirk files in future sessions and avoids known mistakes

**Set up automation with hooks:**
- **PostToolUse hook** -- auto-regenerate quirk files when a lesson is saved
- **Stop hook** -- auto-commit lessons at the end of every session

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "python3 path/to/generate-quirks.py 2>/dev/null || true",
            "timeout": 30,
            "statusMessage": "Regenerating quirks from lessons..."
          }
        ]
      }
    ],
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "cd /path/to/project && git add lessons/ quirks/ && git commit -m 'Auto-save lessons from session' 2>/dev/null || true",
            "timeout": 30,
            "statusMessage": "Saving lessons..."
          }
        ]
      }
    ]
  }
}
```

This turns every session into a knowledge-building loop: you learn, you capture, the system remembers.

### Conversation Management

- **`/compact`** when context gets long -- Claude summarizes the conversation and continues with a compressed version, saving tokens and keeping things fast.
- **Start new sessions for new topics** -- don't let context from an old topic confuse a new one.
- **Read multiple files at once** -- "Read `config.ts`, `schema.sql`, and `README.md`" -- Claude reads them in parallel.
- **Use `@filename`** to reference files without reading them -- Claude knows what you mean.

### Multi-File Workflows

Claude handles large-scale changes across many files:

```
Use agents to implement the new error handling pattern in all 5 service files
```

```
Review all files in src/ for security issues -- use an agent for each directory
```

Agent isolation keeps parallel edits safe. For changes to the same repo, Claude uses git worktrees so agents don't step on each other.

### Cost Optimization

| Strategy | Why it helps |
|:---------|:------------|
| Use `/cost` regularly | Know what you're spending |
| Use Sonnet for simple tasks | Faster and cheaper than Opus |
| Use Opus for complex reasoning | Worth the cost for architecture decisions |
| Use `/compact` on long conversations | Reduces token usage significantly |
| Be specific in your prompts | Less exploration = fewer tokens |

### Debugging with Claude

Claude is an excellent debugger. Give it the error and let it work:

```
Here's the error: [paste error message]. Fix it.
```

```
Run the tests and fix whatever fails
```

```
Check the log file at logs/app.log for errors in the last hour
```

```
The app crashes on startup -- diagnose and fix it
```

**Pro tip:** Claude can read screenshots. If you have an error in a browser or GUI, take a screenshot and paste it directly into the conversation.

### The "Remember This" Pattern

Build up Claude's knowledge of your project over time:

```
Remember that we use bun, not npm
```

```
Remember that the staging API is at port 3001 and requires the VPN
```

```
Remember that Maria on the team prefers camelCase for all variables
```

Check what's saved: `/memory`

Correct mistakes: `"Stop remembering X"` or `"Update memory: we switched from Jest to Vitest"`

Each `"remember"` instruction persists across sessions, so Claude gets smarter about your project the more you use it.

---

## Quick Reference Card

Everything you need on one screen.

| What you want | What to say |
|:--------------|:------------|
| Fix a bug | `"Fix the error on line 42 in app.js"` |
| Add a feature | `"Add a dark mode toggle to the settings page"` |
| Understand code | `"Explain how the auth middleware works"` |
| Refactor | `"Simplify this function -- it's too complex"` |
| Write tests | `"Write tests for the user service"` |
| Git operations | `"Commit this and push to a new branch called feature/dark-mode"` |
| Code review | `"Review the changes I made today"` |
| Search codebase | `"Find all files that import the database module"` |
| Parallel work | `"Use agents to fix these 5 lint errors simultaneously"` |
| Read a file | `"Read src/config.ts and explain it"` |
| Create a file | `"Create a new file at src/utils/logger.ts with a basic logger"` |
| Run a command | `"! npm test"` or `"Run the test suite"` |
| Check spending | `/cost` |
| Switch models | `/model` |
| Compress context | `/compact` |
| Learn something | `"/learn -- explain what Docker containers are"` |
| Build something | `"/build -- I want to automate my weekly report"` |
| Reflect | `"/reflect -- let's capture what I learned today"` |
| Share knowledge | `"/share -- create a guide for my team"` |
| Get help | `"/pathfinder -- what should I do?"` |

---

## Next Steps

1. **Right now:** Open Claude Code and try three commands from Level 1
2. **This week:** Use Claude Code on a real task -- fix a bug, add a feature, or review code
3. **This month:** Set up CLAUDE.md for your project and create your first hook
4. **Ongoing:** Install [Pathfinder Skills](https://github.com/ChewbaccaRoars/pathfinder-skills) and use `/reflect` at the end of each session to track your growth

The best way to learn Claude Code is to use it. Start with something small, break things, fix them, and build from there.
