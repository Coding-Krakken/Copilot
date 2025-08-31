**@copilot — Full PR Audit, Verification, and Gap Closure**

You are acting as a principal engineer reviewer and fixer on this PR. Execute the following loop until the PR is truly production-ready.

### 0) Scope & Ground Rules

* Work **only** within this repository and this PR’s branch.
* Preserve existing behavior unless a bug or spec mismatch requires change; if so, justify it in your notes.
* Keep changes **atomic and well-described**. Push incremental commits for each fix. Avoid noisy refactors unless they directly unblock the PR goal.

### 1) Understand the PR

* Read the **PR title, description, diff, and linked issues**.
* Infer and state the **intended goal/scope** of this PR (functional outcomes, acceptance criteria, success signals).
* List assumptions if spec is unclear.

### 2) Repo-Wide Health Check

Run a full project verification to ensure a clean, functional codebase:

* **Install/setup** per repo instructions.
* **Static checks:** lint, format, type-check.
* **Build:** ensure production build succeeds.
* **Tests:** run unit, integration, and e2e (if present). Capture failing suites/tests with error snippets.
* **Security & quality (if available):** dependency audit, vulnerable patterns, obvious perf anti-patterns.
* **Migrations/DB (if applicable):** generate/apply, verify schema consistency.
* **Local smoke:** boot the app/services, verify key flows relevant to this PR.

### 3) Verify Previously Done Work

* Revisit recent commits in this PR that claimed fixes. Confirm each fix is actually effective (show how you verified).
* Identify any **regressions, flaky tests, or unaddressed TODOs** introduced by this PR.

### 4) Gap Analysis vs. PR Goal

* Compare current behavior to the PR’s intended outcome.
* Produce a **numbered gap list**, each with:

  * **Title** (concise)
  * **Impact** (user risk, correctness, security, perf, DX)
  * **Evidence** (stack traces, failing tests, repro steps, logs)
  * **Proposed Fix** (short plan)
  * **Effort/priority** (High/Med/Low)

### 5) Plan of Attack

* Prioritize gaps by **impact × effort**.
* Draft a **minimal, safe sequence of commits** to close them (commit plan).

### 6) Execute & Iterate

For each gap (highest priority first):

* Implement the fix with **small, atomic commits** (include context in messages).
* Add/adjust **tests** that prove the fix.
* Re-run **lint/type/build/tests** after each fix.
* If a change has cross-cutting effects, document them in the PR comment and update any affected configs/migrations.

### 7) Post Updates to This PR

After Step 2–4 and after each batch of fixes, **add a single consolidated comment** on this PR in the following format:

**PR Audit & Status Update (Automated by Copilot)**

* **PR Goal (interpreted):** <your summary>
* **Repo Health:** Lint ✅/❌ | Types ✅/❌ | Build ✅/❌ | Tests: <passed>/<total> (list failing files/tests)
* **Key Findings:**

  1. <Finding> — Impact: <…> — Evidence: <…>
  2. …
* **Gap List & Plan:**

  1. <Gap Title> — Priority: <…> — Fix: <plan>
  2. …
* **Changes Landed:**

  * <commit hash>: <one-line description>
  * …
* **Next Actions (in order):**

  1. <action>  
  2. …
* **Artifacts:** attach logs/snippets/error excerpts where helpful.

### 8) Definition of Done

* All gaps from Step 4 are closed or explicitly deferred with justification.
* All checks green: **lint, types, build, tests**.
* New/updated tests cover the PR’s goal and prior regressions.
* PR description updated if scope evolved; include a concise **Changelog** of what changed and why.

### 9) If Blocked

* Document blockers with **proof** (error logs, repro steps).
* Propose **unblocking options** (A/B/C) and proceed with the safest minimal option that keeps the PR moving.

**Begin now.** Start by posting the **Step 1–4 summary** as a PR comment, then proceed to implement the Step 5 plan with iterative commits and follow-up status updates until **Definition of Done** is met.
