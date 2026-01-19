---
name: brainstorming
description: Use when the user provides a raw idea, feature request, or problem statement that needs architectural definition before planning.
disable-model-invocation: true
user-invocable: true
---

# Brainstorming Ideas Into Designs

## Overview

This skill converts vague ideas into concrete, committed design documents. It forces a "Measure Twice, Cut Once" discipline by refusing to write code or plans until the architecture is validated.

**Core Principle:** ambiguous requirements lead to buggy code. We eliminate ambiguity through interrogation before we build.

## When to Use

- Use when starting a new feature or project.
- Use when requirements are vague (e.g., "Build a login system").
- Use when the user asks "How should we build X?".

## The Process

### Phase 1: Context & Interrogation

**1. Gather Context**
Before asking questions, read the current project state to avoid asking obvious things.
- `ls -R` key directories.
- Read `README.md` or existing architecture docs.

**2. The Interrogation Loop**
Do not propose a solution immediately. Ask questions to narrow the scope.
- **Rule:** Ask 1-3 targeted questions per turn.
- **Rule:** Prefer multiple-choice questions to reduce user friction.
- **Stop Condition:** When you can articulate the *Data Structure*, *Interface*, and *Edge Cases* clearly.

### Phase 2: Proposal & Trade-offs

Present 2-3 distinct architectural approaches.
- **Option A:** The "Simple/Naive" approach (Fast, minimal deps).
- **Option B:** The "Robust/Scalable" approach (More complex, future-proof).
- **Recommendation:** Explicitly recommend one and explain *why* based on the user's constraints.

### Phase 3: The Design Document

Once an approach is selected, you **MUST** write a design document. Do not skip this.

**Create file:** `docs/designs/YYYY-MM-DD-<topic>-design.md`

**Required Template Structure:**
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

### Phase 4: Validation & Commitment

1. **Present the file content** to the user for review.
2. **Iterate** based on feedback.
3. **Commit the design:**
   ```bash
   git add docs/designs/YYYY-MM-DD-<topic>-design.md
   git commit -m "docs: add design for <topic>"
   ```

## Red Flags - STOP

- **User asks for code immediately:** Refuse. Explain that code written without design is technical debt.
- **"I'll remember the design":** You won't. Write it down.
- **Skipping the commit:** The workflow breaks if the design isn't in git.

## Deliverable

A committed Markdown file in `docs/designs/` containing the approved architecture.
