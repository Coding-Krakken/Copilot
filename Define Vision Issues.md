# Copilot — Create 15 Parallel, Template-Compliant GitHub Issues (Vision-Driven)

**Your role:** Act as a principal engineer and documentation author.
**Your scope:** Only create issue files under `.github/issues/**` using the provided templates. **Do not modify application code. Do not resolve or implement any issue.**

## Objectives

1. **Understand the codebase**

   * Analyze the repository structure, domains, modules, and current capabilities.
   * Identify the intended product by reading code, tests, docs, and configs.

2. **Define an elite-grade vision**

   * Envision the project at the pinnacle of quality, functionality, performance, security, UX, and maintainability—surpassing Google/Microsoft-level bar.
   * Consider big-picture architecture **and** the fine details that add up to world-class polish.

3. **Create 15 high-value, parallelizable issues**

   * Using your vision, propose **the next most valuable 15 issues** that maximize **functional progress** (priority over cosmetic work) while enabling parallel execution without merge conflicts.
   * Each issue must be scoped so its future implementation can proceed largely in isolation (distinct modules, files, or bounded contexts).
   * Distribute issues across the following directories based on intent (use the existing templates in each):

     * `new-features/`, `bug-reports/`, `docs/`, `chores/`, `infra/`, `ux/`, `performance/`, `security/`, `maintenance/`.
   * Favor a functionality-heavy mix (e.g., many `new-features/` + high-impact `bug-reports/`), with the remaining issues covering infra, perf, security, UX, docs, chores, maintenance as appropriate to the repo.

## Hard constraints

* **You are only authoring issue files. Do not implement, refactor, or change code or configuration outside `.github/issues/`.**
* **Use the correct template in each subdirectory** exactly as provided:

  ```
  .github/issues/
  ├─ README.md
  ├─ bug-reports/template.md
  ├─ chores/template.md
  ├─ docs/template.md
  ├─ infra/template.md
  ├─ maintenance/template.md
  ├─ new-features/template.md
  ├─ performance/template.md
  ├─ security/template.md
  └─ ux/template.md
  ```
* **Do not edit `.github/issues/README.md`** (avoids branch conflicts).
* **No secrets or sensitive data** in any issue bodies (especially under `security/`).
* Each issue must be **self-contained**, with clear acceptance criteria and testing guidance, so an engineer can implement it end-to-end.

## File naming & structure

* Create exactly **15 new `.md` files**, each under the appropriate directory.
* Filename format: `YYYYMMDD-###-short-kebab-title.md`

  * `YYYYMMDD` = today’s date
  * `###` = 3-digit sequence `001`..`015`
  * `short-kebab-title` = concise slug (≤ 6 words)
* Example path:

  * `.github/issues/new-features/20250903-001-work-orders-bulk-edit.md`

## Template usage & required sections

* **Start by copying the directory’s `template.md`** and then fill it completely.
* If the template lacks any of the sections below, **append** an “Additional Metadata” section at the end containing them (do not alter the template headings themselves):

  * **Context & Rationale** — why this matters now; link to code dirs/files if helpful.
  * **User/Business Value** — the functional outcome or user story.
  * **Scope (What/Where)** — explicit boundaries; call out non-goals.
  * **Acceptance Criteria** — bullet list or Gherkin-style Given/When/Then.
  * **Implementation Notes (Guidance, not code)** — patterns, modules to touch, migration outline, API contracts at a high level; keep it language-agnostic if uncertain.
  * **Testing Guidance** — unit/integration/e2e; how to verify; data states.
  * **Performance/SLO expectations** (if relevant) — baseline vs target, method of measurement.
  * **Security/Privacy considerations** (if relevant) — threats & mitigations.
  * **Dependencies & Parallelization** — declare any ordering or independence; ensure different future branches won’t collide.
  * **Suggested Branch Name** — `type/short-kebab-title` (e.g., `feat/bulk-edit-work-orders`).
  * **Labels** (as plain text in the file): priority (P0/P1/P2), type (feature/bug/perf/security/etc.).

## Prioritization & distribution (guidance)

* Prioritize **functional enablement** (core flows working end-to-end).
* Propose an approximate mix such as:

  * 7–9 in `new-features/` (functional capabilities that unlock usage),
  * 2–3 in `bug-reports/` (blocking defects),
  * 1–2 in `infra/` or `performance/` (to keep velocity and reliability),
  * 1 in `security/` (hardening a meaningful surface),
  * 1 in `ux/` or `docs/` (to reduce friction).
* Adjust the distribution to **this repo’s** reality after your audit.

## Parallelization rules (avoid future merge conflicts)

* Each proposed issue’s **future implementation** should:

  * Touch distinct modules, routes, or components;
  * Introduce new files rather than mass-editing shared ones;
  * Avoid renames/moves of common shared directories;
  * Confine migrations to its own migration file;
  * Keep API changes backward-compatible when possible.
* Explicitly document any dependency between issues (e.g., “A can proceed without B”).

## Deliverables (in this branch)

1. **Exactly 15 new issue files** created under the correct subdirectories, fully populated per above.
2. **A plaintext summary printed to the chat output** (not a repo file) listing: sequence number, title, target directory, *Suggested Branch Name*, and one-line value statement.

> **Do not create or modify any other files besides the 15 issue files. Do not implement fixes or features. Your task ends when the 15 issue files exist and the summary is printed.**

## Workflow

1. **Audit & Vision** — silently scan the repo and form the elite-grade vision.
2. **Plan** — pick the 15 highest-value, parallelizable issues (functionality-first).
3. **Author issues** — copy the correct template for each directory and fill it out; append “Additional Metadata” if needed.
4. **Self-check** — verify: correct paths, filenames, template filled, acceptance criteria present, scopes independent, no secrets, exactly 15 files.
5. **Output summary** (to chat): table of all 15 with path, title, branch name, and rationale.

## Example (format only — do not reuse content verbatim)

* **Path:** `.github/issues/new-features/20250903-001-bulk-edit-work-orders.md`
* **Suggested Branch:** `feat/bulk-edit-work-orders`
* **One-liner:** Enable supervisors to bulk-edit status/assignees for selected work orders to accelerate triage.

(Body = filled `new-features/template.md` + “Additional Metadata”.)

---

**Important:** Your assignment is to **create issue files only** in the specified locations and **explicitly not to resolve or implement** any of them.
