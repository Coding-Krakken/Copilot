# Development Cycle with Copilot PR Prompts

This repository directory defines a **20-stage development cycle** for guiding GitHub Copilot entirely through Pull Request (PR) comments. The prompts are designed to mirror elite engineering practices at companies like Google, Microsoft, and Stripe, ensuring that every PR is atomic, correct, maintainable, secure, and production-ready.

---

## Table of Contents

- [Philosophy](#philosophy)
- [Workflow Overview](#workflow-overview)
- [Retry Logic](#retry-logic)
- [Prompt Descriptions](#prompt-descriptions)
- [Required vs. Conditional Prompts](#required-vs-conditional-prompts)
- [Diagram](#diagram)
- [Best Practices](#best-practices)

## Philosophy

* **PR-driven development**: all code flows through Pull Requests, never direct pushes.
* **Prompt-guided Copilot**: PR comments instruct Copilot to take actions in sequence.
* **Gated process**: each stage enforces a “Definition of Done.” If a prompt fails, it is retried until CI is green before moving forward.
* **Risk-driven branching**: not all PRs require all 20 prompts. Critical gates (1–4, 14–15) are always run; the others are applied based on what the PR touches.
* **Auditability**: every PR leaves behind tests, docs, commit messages, and ADRs.

---

## Getting Started

To get started with this development cycle:

1. Create a new Pull Request in your repository.
2. Comment on the PR with the first prompt: "@copilot Audit the scope and risks of this PR. Create a 3-step plan: tests → implementation → refactor."
3. Wait for Copilot to respond and implement the changes.
4. Proceed to the next prompts as needed, following the workflow below.

---

## Workflow Overview

1. **Every PR starts with Prompt 1 (Audit & Plan).**
2. **Core sequence (1–4)** must always succeed before any further prompts.
3. **Conditional prompts (5–13, 16–20)** are applied based on scope:

   * e.g., Security (7) only if auth/data touched; Performance (6) only if hot paths touched.
4. **Every PR ends with Docs/ADR/Release Mgmt (14) and Commit Summary (15).**
5. **If a prompt fails, rerun it until successful.** Do not advance until green.
6. **Optional parallelization**: some prompts can run side-by-side after 1–4 succeed.
7. **Finalization**: CI/CD (20) validates the entire pipeline before merge.

---

## Retry Logic

* If Prompt N fails, rerun **only Prompt N** until CI is green.
* Do not roll back earlier successful prompts unless regressions are introduced.
* Refine the prompt if needed to be more specific about what remains broken.
* Example:

  ```
  @copilot Previous attempt didn’t fully succeed. Fix remaining test failures in X.spec.ts and raise coverage above 90%. Do not regress other criteria.
  ```

---

## Prompt Descriptions

| # | Name | Description | Type |
| --- | --- | --- | --- |
| 1 | Audit & Plan | Assess the scope, risks, and create a 3-step plan (tests → implementation → refactor). | Required |
| 2 | Quality Gate & Test Coverage | Fix build, lint, type errors, and ensure ≥90% coverage on touched files. | Required |
| 3 | Test Suite (Unit/Integration/E2E) | Follow the testing pyramid. Add positive, negative, and edge-case tests. | Required |
| 4 | Refactor & Code Clean-up | Remove duplication, simplify logic, improve naming and readability. | Required |
| 5 | Code Style & Best Practices | Enforce project coding standards, SOLID principles, and descriptive naming. | Conditional |
| 6 | Performance & Concurrency | Add benchmarks, optimize hot paths, ensure thread/concurrency safety. | Conditional |
| 7 | Security & Secrets Management | Validate inputs, sanitize outputs, remove hard-coded secrets, add negative tests. | Conditional |
| 8 | Build & CI | Produce immutable artifacts, externalize configs, ensure pipeline runs all gates. | Conditional |
| 9 | Feature Flags & Progressive Delivery | Wrap new features behind flags, default off, document toggling. | Conditional |
| 10 | Dependency & License Management | Upgrade dependencies securely, review licenses, justify new additions. | Conditional |
| 11 | Logging & Observability | Add structured logs, metrics, and traces; document observability practices. | Conditional |
| 12 | Database & Data Integrity | Use safe queries, transactions, and migrations. Test concurrent access. | Conditional |
| 13 | Internationalization & Accessibility | Extract strings, add translations, enforce a11y (ARIA, contrast, keyboard nav). | Conditional |
| 14 | Documentation, ADR & Release Mgmt | Update README/CHANGELOG, write ADRs, bump versions, draft release notes. | Required |
| 15 | Commit Messages & PR Summary | Rewrite commits in Conventional Commits format, generate a clear PR summary. | Required |
| 16 | Contract & Inter-Service Tests | Validate API contracts, ensure backward compatibility, run consumer/provider tests. | Conditional |
| 17 | Error Handling & Resilience | Add robust error handling, retries, backoff, and graceful fallbacks. | Conditional |
| 18 | Infrastructure & IaC | Update versioned infra code, externalize configs/secrets, plan safe deployments. | Conditional |
| 19 | Observability & Monitoring | Add metrics and traces, integrate with dashboards, document monitoring strategy. | Conditional |
| 20 | CI/CD Pipeline & Automation | Validate pipelines run all checks, produce artifacts, and integrate securely. | Conditional |

---

## Usage Examples

Below are scenario-based examples showing how to apply the development cycle to different types of PRs. For each scenario, we outline the key prompts to use, why they're relevant, and sample comments. Remember, required prompts (1-4, 14-15) are always applied; conditionals are selected based on the scenario.

### Scenario 1: Implementing a New Feature (e.g., Adding User Login to a Web App)

**Scope**: Adding a new authentication feature that involves UI, backend logic, and database changes.

**Applicable Prompts**:
- **1-4 (Required)**: Core development and quality.
- **7 (Security)**: Critical for auth features to handle inputs securely.
- **9 (Feature Flags)**: Wrap behind a flag for gradual rollout.
- **12 (Database)**: Ensure safe queries and migrations for user data.
- **14-15 (Required)**: Document and summarize.

**Sample Comments**:
- For 1: `@copilot Audit the login feature PR. Risks include data breaches and UX issues. Plan: 1) Test auth flows, 2) Implement login logic, 3) Refactor for security.`
- For 7: `@copilot Secure the login: validate inputs, sanitize outputs, remove secrets, add tests for SQL injection and XSS.`
- For 14: `@copilot Update docs for the new login feature, write an ADR on auth strategy, bump version to 1.1.0.`

### Scenario 2: Fixing a Critical Bug (e.g., App Crash on Mobile)

**Scope**: Resolving a crash in the mobile app caused by null pointer exception.

**Applicable Prompts**:
- **1-4 (Required)**: Analyze, fix, test, and clean up.
- **6 (Performance)**: Ensure the fix doesn't degrade performance.
- **17 (Error Handling)**: Improve resilience to prevent future crashes.
- **14-15 (Required)**: Document the fix.

**Sample Comments**:
- For 1: `@copilot Audit the crash fix. Risks: incomplete fix causing more issues. Plan: 1) Reproduce and test fix, 2) Implement null checks, 3) Refactor error handling.`
- For 17: `@copilot Add robust error handling: retries for network calls, graceful fallbacks for crashes, and logging for debugging.`
- For 15: `@copilot Rewrite commits as 'fix: resolve null pointer crash in mobile app' and summarize the PR impact.`

### Scenario 3: Security Vulnerability Patch (e.g., Updating Dependencies)

**Scope**: Patching a vulnerability in a third-party library used in the project.

**Applicable Prompts**:
- **1-4 (Required)**: Assess, update, test, and refactor.
- **7 (Security)**: Validate the patch and add security tests.
- **10 (Dependencies)**: Upgrade securely and review licenses.
- **14-15 (Required)**: Document the security update.

**Sample Comments**:
- For 1: `@copilot Audit the security patch. Risks: breaking changes from update. Plan: 1) Test compatibility, 2) Update dependency, 3) Refactor affected code.`
- For 10: `@copilot Upgrade the vulnerable library to the latest secure version. Review licenses and justify the change.`
- For 7: `@copilot Ensure the patch fixes the vulnerability: add negative tests for exploits and validate inputs.`

### Scenario 4: Performance Optimization (e.g., Slow API Response)

**Scope**: Optimizing a slow API endpoint in a backend service.

**Applicable Prompts**:
- **1-4 (Required)**: Plan, implement, test, and clean up.
- **6 (Performance)**: Benchmark and optimize the hot path.
- **11 (Logging)**: Add metrics for monitoring response times.
- **19 (Observability)**: Integrate with dashboards for ongoing monitoring.
- **14-15 (Required)**: Document the optimization.

**Sample Comments**:
- For 1: `@copilot Audit the API optimization. Risks: over-optimization breaking functionality. Plan: 1) Profile and test improvements, 2) Optimize queries, 3) Refactor for maintainability.`
- For 6: `@copilot Add benchmarks for the API endpoint. Optimize database queries and caching to reduce response time by 50%.`
- For 19: `@copilot Add metrics and traces for the API. Integrate with monitoring dashboards and document the strategy.`

These scenarios demonstrate risk-driven application of prompts. Start with required ones, then apply conditionals based on the PR's impact.

---

## Required vs. Conditional Prompts

* **Always required**: 1–4, 14, 15.
* **Conditional**: 5–13, 16–20 (applied only when relevant).

---

## Diagram

A simplified view of the process:

```
[1 Audit & Plan] → [2 Quality Gate] → [3 Tests] → [4 Refactor]
          ↓
  ┌─────────────────────────────────────┐
  │ Conditional Gates (5–13, 16–20)     │
  └─────────────────────────────────────┘
          ↓
 [14 Docs/Release] → [15 Commit Summary]
          ↓
     [20 CI/CD Automation]
```

---

## Best Practices

* Keep PRs **atomic** (one feature or fix per PR).
* Always **document changes** (14) and **summarize commits** (15).
* Apply **conditional prompts** only as needed to avoid overhead.
* Use **reruns** until each gate is fully green.
* Trust **CI output** as the source of truth.

