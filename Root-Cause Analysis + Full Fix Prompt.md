### 🔹 Root-Cause Analysis + Full Fix Prompt (Non-PR Version)

You are acting as a senior engineer responsible for ensuring code quality and stability.

**Your objective:** Identify the *root cause* of the current issue and then deliver a **complete, production-ready fix** that fully resolves it.

---

#### Step 1 — Root Cause Analysis (RCA)

1. **Symptoms & Signals:** List the failing tests, stack traces, error logs, or broken invariants.
2. **First-Bad Change:** From the recent code changes, identify the earliest point where the break was introduced. If uncertain, list the most likely suspects and why.
3. **Causal Chain:** Trace the flow of data, control, contracts, or types from the input to the point of failure. Pinpoint the divergence.
4. **Minimal Reproduction:** Show or describe the smallest example that reproduces the issue.
5. **Risk Analysis:** Recommend the safest, smallest scope location to apply the fix (caller, callee, interface, or boundary).

---

#### Step 2 — Full Solution Implementation

6. **Patch Plan:** Propose and apply a concise, correct fix that addresses the root cause at the right abstraction level.
7. **Regression Tests:** Add or update automated tests that would have caught this issue, ensuring future coverage.
8. **Validation:** Run the full suite of tests, linters, and builds. Confirm all pass. Provide commands and outputs.
9. **Documentation & Notes:** Summarize the root cause, explain the fix, and update any relevant inline comments, changelogs, or docs.

---

**Deliverable:** A working, tested, and documented fix with no remaining gaps, implemented in full.
