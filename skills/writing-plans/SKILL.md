---
name: writing-plans
description: Use when a design document exists and needs to be converted into atomic, test-driven engineering tasks.
disable-model-invocation: true
user-invocable: true
---

# Writing Plans

## Overview

This skill translates a high-level Design Document into a step-by-step TDD implementation plan. It assumes the person executing the plan (you or another agent) has **zero context** and **must** be guided by strict, atomic instructions.

**Core Principle:** A plan is a series of verifications. If a step cannot be verified, it is not a valid step.

## When to Use

- Use **ONLY** after a design document has been created (see `brainstorming`).
- Use before writing any implementation code.

## The Iron Rules of Planning

1.  **Atomic Granularity:** Each step must take 2-5 minutes to execute.
2.  **Test-Driven:** Steps must follow Red-Green-Refactor.
3.  **No "Implement Feature":** specific file edits only.
4.  **No Context Required:** The plan must contain the code snippets or exact logic needed.

## The Process

### Step 1: Read the Design
Read the specific design file from `docs/designs/`. Do not guess the requirements.

### Step 2: Create the Plan File
**Create file:** `docs/plans/YYYY-MM-DD-<topic>-plan.md`

**Required Header:**
```markdown
# Implementation Plan - [Topic]

> **Reference:** `docs/designs/YYYY-MM-DD-<topic>-design.md`
> **Execution:** Use `executing-plans` skill.
```

### Step 3: Write the Tasks (TDD Format)

Break the feature into `Task 1`, `Task 2`, etc. Inside each task, use this **Mandatory Structure**:

```markdown
### Task [N]: [Name]

**Goal:** [One sentence]

**Step 1: Write the Failing Test**
- File: `tests/path/to/test.ts`
- Code:
  ```typescript
  // Paste the EXACT test case code here
  ```

**Step 2: Run Test (Red)**
- Command: `npm test tests/path/to/test.ts`
- Expect: "Fail: function not found"

**Step 3: Implementation (Green)**
- File: `src/path/to/source.ts`
- Action: Write minimal code to pass test.
- Guidance: [Specific logic or snippet]

**Step 4: Verify (Green)**
- Command: `npm test tests/path/to/test.ts`
- Expect: PASS

**Step 5: Git Commit**
- Command: `git add . && git commit -m "feat: [task name]"`
```

### Step 4: Commit the Plan

Once the plan is written:
1.  Ask the user to review the plan.
2.  **Commit the plan:**
    ```bash
    git add docs/plans/YYYY-MM-DD-<topic>-plan.md
    git commit -m "plan: add implementation plan for <topic>"
    ```

## Red Flags - STOP

- **Vague Steps:** "Add validation" is a failure. Write: "Add `if (!email) throw Error` to line 45".
- **Missing Verifications:** Every code change must have a corresponding verification command.
- **Batching too much:** If a task touches >3 files, split it.

## Deliverable

A committed, TDD-structured Markdown file in `docs/plans/`.
