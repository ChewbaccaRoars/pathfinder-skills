# Intern Onboarding: AI Projects with Claude Code

**Audience**: New interns joining the AI Platform team

**Time needed**: 30 minutes to set up, then ongoing

**What you'll walk away with**: A fully configured development environment with Claude Code, GitLab access, and a structured way to capture everything you learn

---

## Welcome

You're joining a team that builds AI-powered tools. You'll be using Claude Code as your daily coding assistant — it can write code, review PRs, run commands, and help you learn. This guide gets you set up and teaches you how to get the most out of it.

---

## Part 1: Setup (15 minutes)

### 1.1 Install Claude Code

Download from [claude.ai/download](https://claude.ai/download) and install it.

Verify it works:
```bash
claude --version
```

### 1.2 Connect to GitLab

Follow the full guide: [Connecting Claude Code to GitLab](claude-code-gitlab-setup.md)

Short version:
1. Install glab: `winget install GLab.GLab` (Windows) / `brew install glab` (Mac)
2. Create a PAT at https://gitlab.cee.redhat.com/-/user_settings/personal_access_tokens (scopes: `api`, `read_user`)
3. Authenticate: `echo "YOUR_TOKEN" | glab auth login --hostname gitlab.cee.redhat.com --stdin`
4. Tell Claude: `allow glab commands`

### 1.3 Clone your project

```bash
git clone https://gitlab.cee.redhat.com/YOUR_GROUP/YOUR_PROJECT.git
cd YOUR_PROJECT
```

### 1.4 Open Claude Code in your project

```bash
claude
```

Claude automatically reads the `CLAUDE.md` file at the root of your project. This file contains architecture decisions, patterns, and lessons learned by everyone who worked on the project before you.

---

## Part 2: Daily Workflow

### Starting your day

Open your project directory and launch Claude Code:
```bash
cd ~/your-project
claude
```

Ask Claude what you need help with in plain English:
- "what does the auth module do"
- "find all the API endpoints in this project"
- "explain how the deployment pipeline works"

### While you're coding

Just describe what you want to build:
- "add a new endpoint that returns user stats"
- "write tests for the login function"
- "this function is too slow, help me optimize it"

When you hit an error:
- Paste the error message and ask "what does this mean and how do I fix it"

### Before committing

Ask Claude to review your changes:
- "review my changes and suggest improvements"
- "create a merge request with a good description"

### End of day

Capture what you learned:
- "journal what I did today" (triggers the iteration journal)
- Claude saves this to memory — it'll remember your context tomorrow

---

## Part 3: The Pathfinder Skills

Claude Code has built-in skills that help you at different stages. You don't need to memorize them — just talk naturally and Claude figures out which one to use. But here's what's available:

### /learn mode

Type `/learn` when you want to understand something.

- Everything technical gets explained in plain English
- Claude flags things you didn't know to ask about
- Safe for experimentation — nothing you do here will break anything

Good for:
- "what is a container"
- "explain REST APIs like I'm 5"
- "what does this Kubernetes yaml actually do"

### /build mode

Type `/build` when you want to create something.

- Helps you find what to build (workflow detective)
- Forms a hypothesis about whether it'll work
- Gets a rough version working fast, then iterates

Good for:
- "I want to automate this spreadsheet update"
- "build a script that checks our CI pipeline"
- "create a dashboard for team metrics"

### /reflect mode

Type `/reflect` at the end of your day or week.

- Captures what you built, what broke, what you learned
- Measures impact (time saved, errors reduced)
- Creates a record you can share with your manager

Good for:
- "journal what I accomplished this week"
- "what's the impact of the automation I built"
- "summarize my progress this sprint"

### /share mode

Type `/share` when you want to show others what you built.

- Creates impact summaries for leadership
- Generates how-to guides for teammates
- Builds workshop outlines for training sessions

Good for:
- "create a summary of my project for the team meeting"
- "help me teach this to another intern"
- "make a presentation about what I built"

---

## Part 4: Updating the Project Knowledge

### Adding to CLAUDE.md

When you learn something important about the project, add it to `CLAUDE.md`. This helps everyone who works on the project after you.

**Architecture decisions**: "We chose X because Y"
```markdown
| 2026-06-15 | Use SQLite instead of PostgreSQL | Simpler for single-user, no server needed | PostgreSQL, MongoDB |
```

**Lessons learned**: "We tried X and it didn't work"
```markdown
| 2026-06-15 | Tried async file writes | Race condition on Windows | Use synchronous writes with file locking |
```

**Patterns**: "Always do X when you encounter Y"
```markdown
- All API responses must include a `status` field
- Never hardcode credentials — use environment variables
```

### Contributing lessons to the team

If you discover something useful that applies beyond your project (like a weird tool behavior or a platform quirk), add it to the team's Training and Enablement repo:

```bash
cd ~/training-and-enablement
# Create a new lesson file
claude  # ask: "help me write a lesson about [what you discovered]"
git add lessons/your-lesson.md
git commit -m "Add lesson: [topic]"
git push
```

---

## Part 5: Getting Help

| Need | Where |
|------|-------|
| Claude Code help | Just ask Claude — it explains itself |
| Git/GitLab help | Ask Claude: "how do I [git thing]" |
| Project-specific questions | Check `CLAUDE.md` first, then ask your mentor |
| Platform issues (VPN, access) | `#help-it-cloud-openshift` on Slack |
| AI model questions | Ask your team lead |

---

## Quick Reference Card

| What you want to do | What to say to Claude |
|---|---|
| Understand code | "explain what [file/function] does" |
| Write code | "create a [thing] that does [behavior]" |
| Fix a bug | paste the error + "how do I fix this" |
| Review changes | "review my changes" |
| Create an MR | "create a merge request" |
| Learn a concept | "/learn" then ask your question |
| Build something | "/build" then describe what you want |
| Journal your day | "/reflect" |
| Share your work | "/share" |
| Find what to automate | "help me find repetitive tasks I could automate" |
