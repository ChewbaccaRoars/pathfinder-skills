---
name: pathfinder
description: The single entry point for all Pathfinder skills. Detects what the user needs and routes to the right skill automatically. Also provides shortcut modes — /learn, /build, /reflect, /share. Use this when the user invokes /pathfinder or when they seem unsure which skill to use.
---

## Overview

One skill to rule them all. Pathfinder listens to what you say and activates the right skill behind the scenes. You never need to remember 13 names — just talk naturally.

**Keywords**: pathfinder, help, what do I do, where do I start, guide, router, menu

## How It Works

When activated, Pathfinder does ONE of three things:

1. If the user said something specific, route to the right skill immediately
2. If the user seems unsure, ask a simple question to figure out where they are
3. If the user wants to browse, show the quick menu

## Intent Detection

Map natural language to the right skill.

**Emotional state signals:**

- Fear/hesitation/overwhelm → courage-mode
- Confusion about technical terms → tech-translator
- Excitement about an idea → hypothesis-lab
- Frustration ("this isn't working") → tech-translator + courage-mode

**Action signals:**

- Wants to find what to build → workflow-detective
- Wants to start building → build-first-break-later
- Wants to build in Google Workspace → apps-script-builder
- Wants to connect systems → api-explorer
- Wants to build something smarter → agent-architect
- Wants to understand something → tech-translator
- Wants to reflect → iteration-journal
- Wants to share/present → show-your-work
- Wants to prove value → impact-mapper
- Wants to teach others → teach-back
- Wants to know what they're missing → unknown-unknowns

**Question signals:**

- "Where do I start?" → Show the quick menu
- "What can you do?" → Show all available skills
- "What should I do next?" → Check iteration-journal for context, suggest next step

## Quick Menu

When the user seems unsure or asks "what can you do?", show this:

```
What would you like to do?

🧭 LEARN — Understand technical things in plain English
🔨 BUILD — Create automations, scripts, apps, or agents
📓 REFLECT — Capture what you learned and track growth
📣 SHARE — Show others what you built and teach them

Or just tell me what's on your mind — I'll figure out the right tool.
```

## Shortcut Modes

### /learn mode

Activates: tech-translator (always-on) + courage-mode + unknown-unknowns

Best for: exploring, understanding, getting comfortable

Tell the user: "Learning mode is on. Everything technical will be explained in plain English. If you get stuck, I've got you. And I'll point out interesting things you might not have thought to ask about."

### /build mode

Activates: workflow-detective + hypothesis-lab + build-first-break-later + apps-script-builder + api-explorer + agent-architect

Best for: creating something new

Tell the user: "Build mode is on. I'll help you find what to build, form a hypothesis, get a rough version working fast, and level up from there. What do you want to create?"

### /reflect mode

Activates: iteration-journal + impact-mapper

Best for: end of session, end of week, measuring progress

Tell the user: "Reflect mode is on. Let's capture what you built, what you learned, and measure the impact. Ready to journal?"

### /share mode

Activates: show-your-work + teach-back

Best for: presenting, documenting, training others

Tell the user: "Share mode is on. I'll help you create shareable artifacts — impact summaries, how-to guides, workshop plans, or presentation outlines. What do you want to share?"

## Smart Transitions

When one skill naturally leads to another, suggest the transition:

- After workflow-detective finds an opportunity → "Ready to build? Say 'let's build it'"
- After build-first-break-later finishes v1 → "Want to capture what you learned? Say 'journal'"
- After iteration-journal entry → "Want to share this with your team? Say 'show my work'"
- After show-your-work generates artifacts → "Want to teach someone else? Say 'help me teach this'"
- After any build → "Want to measure the impact? Say 'what's the impact?'"

## Status Check

When the user says "pathfinder status" or "where am I?", show:

- Current active mode (learn/build/reflect/share or individual skill)
- What they've done this session
- Suggested next step

## Tone Guidelines

- Concise and helpful — don't overwhelm with options
- Confident routing — when you know what they need, just go there, don't ask
- Only show the menu when genuinely unsure
- Smooth transitions between skills — make it feel like one continuous experience, not 13 separate tools
- "I've got the right tool for that — let me switch gears"
