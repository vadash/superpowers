---
name: brainstorming
description: Converts raw ideas into committed design documents through structured interrogation. Use when a user provides a feature request, problem statement, or asks "how should we build X", "design X", or "I have an idea for X".
disable-model-invocation: true
user-invocable: true
---

# Brainstorming Ideas Into Designs

## Instructions

This skill converts vague ideas into concrete, committed design documents. It refuses to write code or plans until the architecture is validated.

**Core Principle:** Ambiguous requirements lead to buggy code. Eliminate ambiguity through interrogation before building.

### Step 1: Gather Context

Before asking questions, read the current project state to avoid asking obvious things.
- `ls -R` key directories.
- Read `README.md` or existing architecture docs.

### Step 2: Interrogation Loop

Do not propose a solution immediately. Ask questions to narrow the scope.
- Ask 1-3 targeted questions per turn.
- Prefer multiple-choice questions to reduce user friction.
- **Stop Condition:** When you can articulate the *Data Structure*, *Interface*, and *Edge Cases* clearly.

### Step 3: Propose Trade-offs

Present 2-3 distinct architectural approaches.
- **Option A:** The "Simple/Naive" approach (fast, minimal deps).
- **Option B:** The "Robust/Scalable" approach (more complex, future-proof).
- **Recommendation:** Explicitly recommend one and explain *why* based on the user's constraints.

### Step 4: Write the Design Document

Once an approach is selected, write a design document. Do not skip this.

**Create file:** `docs/designs/YYYY-MM-DD-<topic>-design.md`

**Required Template:**
```markdown
# Design: [Topic]

## 1. Problem Statement
What are we solving?

## 2. Goals & Non-Goals
- Must do: ...
- Won't do: ...

## 3. Proposed Architecture
- High-level approach
- Key components

## 4. Data Models / Schema
(Use code blocks for JSON/SQL schemas)

## 5. Interface / API Design
(Function signatures, API endpoints)

## 6. Risks & Edge Cases
- What happens if network fails?
- What if input is empty?
```

### Step 5: Validate and Commit

1. Present the file content to the user for review.
2. Iterate based on feedback.
3. Commit the design:
   ```bash
   git add docs/designs/YYYY-MM-DD-<topic>-design.md
   git commit -m "docs: add design for <topic>"
   ```

## Red Flags - STOP

- **User asks for code immediately:** Refuse. Code written without design is technical debt.
- **"I'll remember the design":** You won't. Write it down.
- **Skipping the commit:** The workflow breaks if the design isn't in git.

## Deliverable

A committed Markdown file in `docs/designs/` containing the approved architecture.
