> **@copilot — Root-Cause First, Then Implement Fully**
>
> **Objective:** Identify the *root cause* of the breaking change, then deliver a **complete, production-ready solution** that resolves it entirely.
>
> **Step 1 — Root Cause Analysis (RCA)**
>
> 1. **Symptoms & Signals:** List failing tests, stack traces, error logs, and the precise invariant being violated.
> 2. **First-Bad Change:** From this PR’s diff and commit history, identify the earliest change that introduced the break. If uncertain, list the top 2–3 suspects with reasoning.
> 3. **Causal Chain:** Trace the flow (data, control, contracts, or typing) from input → failure, pinpointing where behavior diverges.
> 4. **Minimal Reproduction:** Show (or describe) the smallest case that reproduces the failure.
> 5. **Risk Analysis:** Recommend the smallest, safest point to apply the fix (caller, callee, boundary, or interface).
>
> **Step 2 — Full Solution Implementation**
> 6\. **Patch Plan:** Provide and apply a concise, correct fix that fully resolves the root cause at the right abstraction level.
> 7\. **Regression Tests:** Add or update automated tests that would have caught this issue, ensuring it never regresses.
> 8\. **Validation:** Run all tests, linters, and builds, and confirm the system is green. Include commands and results.
> 9\. **Documentation & Notes:** Summarize the root cause, the fix applied, and why it is correct and minimally invasive. Update any relevant comments, docs, or READMEs.
>
> **Deliverable:** A fully working, tested, and documented fix merged into the codebase, with no remaining gaps.


