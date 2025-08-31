# **Universal Copilot Prompt (Strategic Gap-Oriented PR Workflow)**

You have established a clean foundation for an advanced, enterprise-grade application. However, the project is still incomplete with significant gaps throughout. Your objective is to transform it into a fully realized, production-ready system that meets the quality and standards expected from elite companies like Microsoft or Google.

Follow this structured execution loop:

---

### **Phase 1 — Audit & Assessment**

* Examine the current codebase, architecture, and functionality.
* Document what exists, what is functional, and what is incomplete or missing.
* Identify potential risks, weaknesses, or technical debt.

---

### **Phase 2 — Vision Definition**

* Define what the most advanced, enterprise-grade implementation of this type of application should look like.
* Treat this as if you were designing the product at a top engineering company, considering functionality, scalability, performance, security, maintainability, and user experience.

---

### **Phase 3 — Gap Identification & Prioritization**

* Compare the current state (Phase 1) against the vision (Phase 2).
* Identify all gaps, then **determine the single most valuable gap to close next**, considering dependencies, impact, and alignment with the vision.

---

### **Phase 4 — Task Decomposition**

* Break the chosen gap down into a **sequence of small, manageable, logically ordered tasks**.
* Each task should be concise, actionable, and valuable on its own while contributing to closing the larger gap.

---

### **Phase 5 — PR-Driven Execution**

* Open a new Pull Request to begin addressing the gap.
* For **Task 1**, create the first **detailed PR comment** that instructs Copilot exactly what to implement.
* That PR comment must explicitly include instructions such as:

  * *“After implementing Task 1, verify the work is functional and valuable, ensuring that all tests, linting, and quality checks pass before continuing.”*
  *  *"After Task 1 is validated, move to Task 2."*
* For **each subsequent task**, add a **new PR comment** with detailed instructions for Copilot.
* Each PR comment must:

  * Be concise yet detailed.
  * Clearly define the task.
  * Include validation requirements written as instructions inside the comment, e.g.,
    *“After completing this task, run all tests, validations, and quality checks. If issues are found, fix them before continuing. Once validated, proceed to the next PR comment/task in sequence.”*
  * Emphasize verifying the prior task’s success before proceeding.

---

### **Phase 6 — Validation & Iteration**

* Each PR comment must also instruct Copilot to perform the following after every task:

  * *“Run all tests, validations, and quality checks.”*
  * *“If issues are found, fix them before continuing.”*
  * *“Once validated, proceed to the next PR comment/task in sequence.”*
* When the current gap is fully closed, the final PR comment for that gap must instruct:

  * *“Return to Phase 3 to select the next most valuable gap and repeat the loop.”*

---

### **Final Objective**

Through this structured, PR-driven loop, evolve the application **gap by gap** into a fully realized, enterprise-grade system. Each step adds validated, production-quality value, and the **PR comments themselves clearly tell Copilot exactly how to proceed, validate, and continue.**

