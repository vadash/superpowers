---
name: executing-plans
description: Executes a TDD implementation plan with strict step-by-step adherence. Use when a plan file exists in docs/plans/ and you are ready to write code, or when user says "go ahead", "start coding", "execute the plan", or "implement the plan".
disable-model-invocation: true
user-invocable: true
---

# Executing Plans

## Instructions

This skill executes a written plan with robotic precision. It prevents "cowboy coding" by enforcing strict adherence to the committed plan.

**Core Principle:** Trust the plan. If the plan is wrong, stop and fix the plan — do not improvise code.

### Step 1: Preparation

1. **Read the Plan:** Load the target file from `docs/plans/`.
2. **Clean State:** Ensure `git status` is clean before starting.
3. **Announce:** "I am starting execution of [Plan Name]. I will stop for feedback after every [N] tasks."

### Step 2: The Execution Loop

**For each task in the plan:**

1. **Read the Step:** Read the specific instructions for the current step.
2. **Execute:**
   - If it says "Write Test", write exactly that test.
   - If it says "Run Command", run exactly that command.
3. **Verify Output:**
   - **CRITICAL:** Check the output of verification commands.
   - **If Verification Fails (Unexpectedly):** STOP. Debug. Do not proceed to the next step.
4. **Commit:**
   - Perform the git commit as specified in the plan.
   - *Self-Correction:* If the plan forgot a commit step, perform one anyway after the task turns Green.

### Step 3: Checkpoints

Every 1-3 tasks (depending on complexity):
1. **Stop.**
2. **Report:** "Completed Task N. Tests passed. Commits created."
3. **Ask:** "Proceed to Task N+1?"

### Step 4: Completion

1. **Final Verification:** Run the full test suite (`npm test` or equivalent) to ensure no regressions.
2. **Summary:** List all created files and commits.

## Red Flags - STOP

- **Verification fails but you proceed:** You are breaking the build. Stop.
- **Modifying files not in the plan:** You are guessing. Stop.
- **Skipping commits:** You are risking work loss. Commit often.

## Common Rationalizations

| Rationalization | Reality |
|-----------------|---------|
| "I can just fix this small bug while I'm here" | Scope creep kills projects. Stick to the plan. |
| "I'll run the tests at the end" | Failures compound. Test at every step. |
| "The plan is slightly wrong, I'll just improvise" | Update the plan file first, *then* execute. Keep documentation in sync. |

## Deliverable

A series of git commits matching the plan, with a clean, passing test suite.
