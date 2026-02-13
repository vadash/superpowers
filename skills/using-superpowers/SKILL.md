---
name: using-superpowers
description: Establishes skill discovery and invocation discipline. Use at the start of any conversation, before any response or action, to ensure relevant skills are checked and loaded via the Skill tool.
---

# Using Skills

## The Rule

**CRITICAL: If there is even a 1% chance a skill applies, you MUST invoke it before responding.**

This is non-negotiable. Invoke relevant skills BEFORE any response, including clarifying questions. If an invoked skill turns out to be wrong for the situation, you don't need to follow it.

## How to Access Skills

**In Claude Code:** Use the `Skill` tool. When you invoke a skill, its content is loaded and presented to you — follow it directly. Never use the Read tool on skill files.

## Instructions

### Step 1: Receive User Message

Check: might any skill apply to this task?

### Step 2: Invoke Skills

If yes (even 1% chance): invoke the Skill tool for each relevant skill.
If definitely not: respond directly.

### Step 3: Announce

State: "Using [skill] to [purpose]"

### Step 4: Follow the Skill

If the skill has a checklist, create a TodoWrite todo per item. Then follow the skill's instructions exactly.

## Skill Priority

When multiple skills could apply:

1. **Process skills first** (brainstorming, debugging) — these determine HOW to approach the task
2. **Implementation skills second** — these guide execution

"Let's build X" → brainstorming first, then implementation skills.
"Fix this bug" → debugging first, then domain-specific skills.

## Skill Types

**Rigid** (TDD, debugging): Follow exactly. Don't adapt away discipline.

**Flexible** (patterns): Adapt principles to context.

The skill itself tells you which.

## Red Flags

These thoughts mean STOP — you're rationalizing:

| Thought | Reality |
|---------|---------|
| "This is just a simple question" | Questions are tasks. Check for skills. |
| "I need more context first" | Skill check comes BEFORE clarifying questions. |
| "Let me explore the codebase first" | Skills tell you HOW to explore. Check first. |
| "This doesn't need a formal skill" | If a skill exists, use it. |
| "I remember this skill" | Skills evolve. Read current version. |
| "The skill is overkill" | Simple things become complex. Use it. |
| "I'll just do this one thing first" | Check BEFORE doing anything. |
| "I know what that means" | Knowing the concept ≠ using the skill. Invoke it. |

## User Instructions

Instructions say WHAT, not HOW. "Add X" or "Fix Y" doesn't mean skip workflows.
