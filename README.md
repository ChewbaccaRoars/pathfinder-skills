# Pathfinder Skills

A collection of Claude Code skills that turn non-technical people into builders — creating their own automations, apps, and agents.

> *"We are not caretakers of the past. We are obsessive learners, compulsive experimenters, and builders of what's next."*

Built for people who believe the AI-native future will be shaped not only by developers, but by business people who learn to build. These skills take someone from "I've never opened a terminal" to "I just built an agent that reimagined our workflow."

## The Skills (13)

### The On-Ramp

<details>
<summary><strong>tech-translator</strong> — Your friendly guide to all things technical</summary>

Translates every command, error, code snippet, and technical concept into plain, everyday language. Designed for someone who has never opened a terminal before.

**Key features:**
- **One-liner analogies**: Every command gets a real-world comparison (e.g., `grep` is "like Ctrl+F for files")
- **Step-by-step breakdowns**: Multi-part commands explained piece by piece
- **Safety labels**: `[SAFE]`, `[REVERSIBLE]`, `[CAUTION]` on every action so you always know the risk
- **Difficulty ratings**: `[Beginner]`, `[Intermediate]`, `[Advanced]` tags set expectations
- **Code comments**: All generated code includes plain-English comments on every function and key line
- **Implementation walkthroughs**: Full setup instructions with exact clicks and menu paths — never just "here's your code"
- **Personal glossary**: Tracks terms you've learned and shortens explanations as you master them
- **Progress tracking**: Adapts depth based on your experience — introduced, learning, mastered
- **Quiz mode**: 3-5 multiple choice questions to reinforce what you've learned
- **ELI5 mode**: Zero-jargon explanations using only everyday analogies
- **Cheat sheet generator**: One-page reference of everything covered in a session
- **Platform-aware**: Adapts instructions to Windows, Mac, or Linux automatically

**Say**: "explain that", "what does that mean", "teach me about git", "quiz me", "ELI5", "cheat sheet"

</details>

<details>
<summary><strong>courage-mode</strong> — For when you're stuck or afraid to start</summary>

Detects when you're hesitant, overwhelmed, or afraid of breaking something, then gently guides you forward with tiny, safe steps.

**Key features:**
- **Hesitation detection**: Recognizes phrases like "I'm scared", "this is too hard", "what if I break something"
- **Reframing**: Turns "I'm stuck" into "You're at the edge of what you know — that's where growth happens"
- **Smallest safe step**: Breaks any intimidating task into the tiniest possible action that's clearly SAFE or REVERSIBLE
- **Safety net**: Before any action, explains exactly how to undo it
- **Progressive courage**: Each small success builds toward the bigger goal
- **Courage tracker**: Remembers when you pushed through fear so it can reference it later — "Remember last week when you were nervous about APIs? Look at you now."
- **Comfort analogies**: "Remember the first time you used a spreadsheet? That felt hard too."

**Say**: "I'm stuck", "I'm scared", "help me start", "this is too hard", "I can't do this"

</details>

### The Learning Loop

<details>
<summary><strong>hypothesis-lab</strong> — Structure every project as an experiment</summary>

Turns every project into a structured experiment so you learn whether your idea actually works — not just whether the code runs.

**Key features:**
- **Hypothesis framework**: "If [we build this], then [this outcome], because [this reason]"
- **Assumption surfacing**: Lists every assumption and labels them `[VERIFIED]`, `[UNTESTED]`, or `[RISKY]`
- **Success criteria**: Defines measurable outcomes before building
- **Minimum test**: Builds the smallest possible version that tests the hypothesis
- **Evidence gathering**: Returns to the hypothesis after building — did it match? What surprised us?
- **Iteration or pivot**: Uses evidence to decide — confirm, adjust, or try something else
- **Experiment log**: Running tracker of all experiments, results, and learnings across sessions

**Say**: "I have an idea", "I want to build something", "let's try something", "what if we..."

</details>

<details>
<summary><strong>build-first-break-later</strong> — Anti-perfectionism by design</summary>

Gets a rough working version into your hands in minutes, then coaches you through improving it. The first version is supposed to be ugly.

**Key features:**
- **60-second capture**: Asks exactly ONE question — "What do you want to build?" — then starts building immediately
- **Simplest tool selection**: Picks the easiest path (Apps Script, Python, HTML) and explains why
- **Rough v1**: Builds fast with hardcoded values, no error handling, no edge cases — intentionally imperfect
- **Break-and-learn loop**: Run it, see what happens, make ONE change, repeat
- **Anti-pattern redirection**: Gently steers away from perfectionism — "Let's handle that in v2"
- **Progress celebration**: "Look at what you just did — you went from an idea to a working thing in 10 minutes"

**Say**: "let's just build it", "start building", "I want a quick prototype", "just make something"

</details>

<details>
<summary><strong>unknown-unknowns</strong> — Discover what you didn't know to ask</summary>

After any build or exploration, proactively surfaces adjacent ideas, hidden risks, and unexpected opportunities you haven't considered.

**Key features:**
- **Adjacent capabilities**: "Your script can also create calendar events, not just read them"
- **Edge cases**: "What happens when the spreadsheet is empty?"
- **Scale questions**: "This works for 10 rows — what happens at 10,000?"
- **Connection opportunities**: "This data also exists in another system — you could pull from both"
- **Security awareness**: "This script has access to your entire Gmail — worth understanding the permissions"
- **Depth adaptation**: Adjusts based on experience level — beginners get opportunities, advanced get architecture questions
- **Never overwhelming**: Maximum 3 unknown unknowns at a time, each framed as an opportunity

**Say**: "what am I missing?", "what else?", "what could go wrong?", "surprise me"

</details>

<details>
<summary><strong>iteration-journal</strong> — Track your growth as a builder</summary>

A structured reflection tool that captures what you built, what broke, what you learned, and what to try next. Tracks growth over time.

**Key features:**
- **Structured entries**: Date, what you built, what worked, what broke, key insight, next hypothesis, confidence level (1-5)
- **Persistent memory**: Entries save across sessions so your learning history grows
- **Weekly summaries**: Aggregates entries and surfaces patterns — "Your confidence with APIs went from 2 to 4 this week"
- **Growth visualization**: Tracks mastered topics, developing skills, and confidence trajectories
- **Look-back feature**: "Show me what I was working on a month ago" — demonstrates your progress

**Say**: "journal", "reflect", "what did I learn today?", "weekly summary", "look back"

</details>

### The Builder Tools

<details>
<summary><strong>workflow-detective</strong> — Find the highest-value thing to automate</summary>

Investigates your daily work to uncover repetitive tasks, bottlenecks, and pain points, then helps you decide what to build first.

**Key features:**
- **Guided investigation**: "Walk me through your Monday morning — what do you do first?"
- **Pattern recognition**: Identifies repetitive tasks, manual data transfers, copy-paste patterns, approval bottlenecks
- **Effort vs. impact scoring**: Plots opportunities on a 2x2 matrix — low effort + high impact = build this first
- **Hard choice forcing**: "You can't build everything — which one matters most?"
- **Prioritized build list**: Top 3-5 opportunities ranked by value, with estimated effort and impact

**Say**: "what should I build?", "help me find automation opportunities", "workflow audit"

</details>

<details>
<summary><strong>apps-script-builder</strong> — Your Google Workspace automation workshop</summary>

A dedicated Google Apps Script assistant that walks non-technical users through building projects from zero. Knows every service, trigger, and deployment pattern.

**Key features:**
- **Full service reference**: Gmail, Sheets, Calendar, Drive, Slides, Forms, Docs — when to use each and whether it needs manual enabling
- **Complete setup walkthroughs**: Opening the editor, enabling services, pasting code, approving permissions — with exact menu paths
- **CLASP guide**: How to install and use the command-line tool for managing Apps Script from your computer (with VS Code, Claude Code, or git)
- **Trigger explanations**: Time-based, on-edit, on-form-submit, on-open — explained in plain English with setup steps
- **Deployment guide**: Test vs. live, web apps, sharing scripts, updating deployments
- **6 common recipes**: Email automation, report generator, form processor, calendar manager, document generator, Slack/webhook integration
- **Patterns reference**: Battle-tested code patterns for spreadsheet ops, email sending, dashboards, API caching, CSV parsing, and more
- **Error translation table**: Common Apps Script errors explained in plain English with fixes
- **Plain-English code comments**: Every generated script is fully commented

**Say**: "build an apps script", "automate my spreadsheet", "connect my Gmail", "send emails from a sheet"

</details>

<details>
<summary><strong>api-explorer</strong> — APIs are friendlier than they look</summary>

Demystifies APIs for non-technical people, from "what is an API?" to making your first call to connecting work systems.

**Key features:**
- **Core analogy**: "An API is like a drive-through window — you place an order in a specific format and get back exactly what you asked for"
- **HTTP methods explained**: GET = "asking a question", POST = "submitting a form", PUT = "updating your address", DELETE = "canceling an order"
- **Status codes explained**: 200 = "thumbs up", 404 = "that page doesn't exist", 401 = "show your ID first", 500 = "broke on their end"
- **JSON explained**: "A way of organizing data that computers can read — like a very structured form"
- **Guided first call**: Step-by-step walkthrough using a free public API (no signup required)
- **Progressive complexity**: Free APIs (weather, quotes) to Google APIs to work APIs (ServiceNow, Jira, Slack)
- **Authentication guide**: API keys, tokens, OAuth — each explained with analogies
- **Error troubleshooting**: What went wrong, what it means, how to fix it

**Say**: "what is an API?", "connect to an API", "make an API call", "how do APIs work?"

</details>

<details>
<summary><strong>agent-architect</strong> — Graduate from scripts to agents</summary>

Guides you from simple automations to building your own agents through six progressive levels, each with a concrete project.

**Key features:**
- **Core analogy**: "An agent is like hiring a virtual assistant who follows your exact instructions"
- **Six levels**:
  - Level 1: A script that checks and acts ("if inbox has email from X, move to folder Y")
  - Level 2: Multi-step workflows (do A, then B, then C)
  - Level 3: Decision logic (if this, do that; otherwise do something else)
  - Level 4: Error handling and recovery
  - Level 5: Connecting multiple systems
  - Level 6: Full agent — autonomous, scheduled, self-monitoring
- **Gradual concept introduction**: APIs, webhooks, scheduling, state management, logging — each with a real-world analogy
- **Milestone moment**: "You just built your first agent. It's small, but it's real."

**Say**: "build an agent", "level up", "what's an agent?", "I want to build something smarter"

</details>

### The Multipliers

<details>
<summary><strong>show-your-work</strong> — Turn builds into organizational knowledge</summary>

Generates shareable artifacts from what you built so your impact multiplies across the organization.

**Key features:**
- **5 output formats**:
  - **Impact Summary** — concise Slack-ready summary with before/after metrics
  - **How-to-Replicate Guide** — step-by-step instructions someone else can follow
  - **Before/After Comparison** — visual table showing the transformation
  - **Learning Story** — narrative of the journey (what broke, what surprised, what you learned)
  - **Presentation Outline** — structured 5-minute demo script with slides
- **Format recommendation**: Suggests the right format based on audience (Slack, teammate, manager, culture post)
- **Jargon-free**: All artifacts written for non-technical audiences
- **Hero framing**: Makes you the hero of the story — you built this

**Say**: "help me share this", "show my work", "write up what I built", "how do I present this?"

</details>

<details>
<summary><strong>teach-back</strong> — Help others build too</summary>

Turns you from a builder into a teacher. Generates everything you need to teach what you built to others.

**Key features:**
- **Teach-back test**: Challenges you to explain what you built in plain words, then coaches you on simplifying
- **Teaching guide**: Structured lesson plan with hook, demo, build-along, and "aha moment"
- **Workshop format**: Full agenda for 30/60/90-minute group sessions with facilitator tips
- **Train-the-trainer kit**: Handoff materials for someone else to teach without you — common questions, common mistakes, troubleshooting guide
- **Practical tips**: "Go slower than you think", "Walk to their screen instead of shouting instructions", "Celebrate every success"

**Say**: "help me teach this", "create a workshop", "train the trainer", "how do I explain this?"

</details>

<details>
<summary><strong>impact-mapper</strong> — Prove the value of what you built</summary>

Quantifies the impact of your builds — time saved, errors reduced, ROI — and generates reports that leadership actually reads.

**Key features:**
- **Pre-build estimation**: Calculates current cost (time x frequency x people) before you start building
- **Post-build measurement**: Compares estimates vs. actuals with real data
- **6 impact categories**: Efficiency, Quality, Speed, Scale, People, Risk
- **Impact report generator**: Executive summary, problem/solution, measured metrics, qualitative feedback, replicability assessment
- **Honest assessment**: If the impact is small, says so and helps find higher-value opportunities
- **Business language**: Frames everything in terms leadership cares about — hours, dollars, risk reduction

**Say**: "what's the impact?", "how much time does this save?", "generate impact report", "show the ROI"

</details>

## The Journey

```
 courage-mode          "I'm scared to start"
      |
 tech-translator       "What does that mean?"
      |
 workflow-detective     "What should I build?"
      |
 hypothesis-lab         "What do I think will happen?"
      |
 build-first-break-later "Let's just build it"
      |
 unknown-unknowns       "What am I not seeing?"
      |
 iteration-journal      "What did I learn?"
      |
 apps-script-builder    "Let me build something real"
 api-explorer           "Let me connect systems"
      |
 agent-architect        "Let me build something smart"
      |
 show-your-work         "Let me share what I built"
 impact-mapper          "Let me prove the value"
      |
 teach-back             "Let me help others build too"
```

## Installation

### Option 1: Install all skills as a Plugin (recommended)

```bash
/plugin install ChewbaccaRoars/pathfinder-skills
```

### Option 2: Install individual skills manually

```bash
# Replace <skill-name> with any skill from the list above
mkdir -p ~/.claude/skills/<skill-name>
cp skills/<skill-name>/SKILL.md ~/.claude/skills/<skill-name>/SKILL.md
```

### Option 3: Project-level (shared with your team via git)

```bash
# Copy all skills into your project
cp -r skills/ .claude/skills/
git add .claude/skills/
git commit -m "Add Pathfinder skills"
```

## Quick Start

1. Install the plugin (see above)
2. Start a new Claude Code session
3. Tech Translator will ask if you want it always-on, on-demand, or off
4. Say "what should I build?" to start with Workflow Detective
5. Say "let's build it" to jump into Build First, Break Later
6. Say "what did I learn?" at the end to reflect with Iteration Journal

## Trigger Phrases (all skills)

| Say this | Skill that activates |
|:---------|:---------------------|
| "explain that" / "what does that mean" | tech-translator |
| "I'm stuck" / "I'm scared" / "this is too hard" | courage-mode |
| "I have an idea" / "I want to build something" | hypothesis-lab |
| "let's just build it" / "start building" | build-first-break-later |
| "what am I missing?" / "what else?" | unknown-unknowns |
| "what should I build?" / "workflow audit" | workflow-detective |
| "build an apps script" / "automate my spreadsheet" | apps-script-builder |
| "what is an API?" / "connect to an API" | api-explorer |
| "build an agent" / "level up" | agent-architect |
| "help me share this" / "show my work" | show-your-work |
| "help me teach this" / "create a workshop" | teach-back |
| "what's the impact?" / "show the ROI" | impact-mapper |
| "journal" / "what did I learn today?" | iteration-journal |
| "quiz me" / "cheat sheet" / "ELI5" | tech-translator |

## Values

These skills are built on a set of beliefs:

- **Learning is not optional.** It's how we grow, adapt, and improve.
- **We learn by doing.** Not by reading. Not by watching. By building.
- **We begin with hypotheses, not certainties.** We test what we believe. We let evidence sharpen our thinking.
- **We respect the unknown.** The best discoveries come from questions we didn't know to ask.
- **We are teachers.** Knowledge grows when it's shared. People grow when they're believed in.
- **We seek transformative outcomes.** We're not here to preserve the status quo. We're here to create meaningful change.

## Contributing

PRs welcome! Whether it's better analogies, new skills, additional trigger phrases, or improvements to existing ones — open an issue or submit a PR.

## License

MIT
