@chatgpt — Generate Comprehensive PR Comments

Context & Vision Source:  
Use the **entire current chat history** as the full product vision and requirements. Treat every detail here as authoritative for what needs to be built.

Output Requirements:  

1. **Initial Umbrella PR Comment**  
   - Write a comprehensive overview comment (≥300 words).  
   - Summarize the complete product vision from this chat.  
   - Break down work into **phases**.  
   - Under each phase, explicitly list all **individual tasks** that must be implemented.  
   - Provide a **Master Acceptance Criteria Checklist** covering:  
     - ✅ Functionality  
     - ✅ Tests (unit, integration, regression, coverage >90%)  
     - ✅ CI/CD passing  
     - ✅ Documentation (README, ADRs, diagrams, changelogs)  
     - ✅ Refactoring of touched code  
     - ✅ Accessibility and compliance  
     - ✅ Security validations  

2. **Sequential Task Comments**  
   For each individual task:  
   - Generate a PR comment (≥300 words).  
   - Begin with **@copilot — Phase X, Task Y: [Task Title]**.  
   - State the **objective** of this task.  
   - Provide **step-by-step implementation instructions**.  
   - Explain **why** each step matters, dependencies, and risks.  
   - Include **best practices** (atomic commits, incremental verification).  
   - End with a **Strict Acceptance Checklist** for that task:  
     - ✅ Task-specific implementation complete  
     - ✅ Tests added (unit + integration where applicable)  
     - ✅ CI/CD passing with no warnings  
     - ✅ Documentation updated (README, ADRs, changelog, diagrams if relevant)  
     - ✅ Code refactored for clarity and maintainability  
     - ✅ Security/lint/type checks clean  
     - ✅ Accessibility compliance (if UI-related)  

3. **Execution Flow**  
   - Step 1: Generate the **Umbrella PR Comment** first.  
   - Step 2: Generate **Sequential Task Comments**, one for each task in order.  
   - Step 3: Continue until every task across all phases has its own PR comment.  

4. **Style & Quality**  
   - Each comment must be **≥300 words** of meaningful, actionable, and instructive content.  
   - No filler — every paragraph must add value (what, how, why, risks, acceptance criteria).  
   - Format with **headers, ordered lists, and checklists** for clarity.  
