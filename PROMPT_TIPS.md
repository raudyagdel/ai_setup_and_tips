# Prompt Guide 

## 🆕 For Starting a New Project

### 🔹 Phase 1 – Architecture & Analysis

Act **strictly** following the rules defined in:

* `.copilot/copilot-instructions.md`
* `AGENTS.md`

Assume the roles of:

* **Architect Agent**
* **Refactor Agent**

**Objective**:

Refactor (or design) the Spring Boot project so it fully complies with the architecture, conventions, and constraints defined in the documents above.

**Rules**:

* Do **not** invent new layers, modules, or technologies that are not explicitly defined.
* Do **not** change existing functionality.
* Respect the boundaries of each module.
* Clearly explain every proposed change.
* If something cannot be done without breaking the rules, **stop and explain why**.

**Start with**:

1. Analysis of the current project structure
2. Identification of violations against the instructions
3. Step-by-step refactor proposal (**no code yet**)

---

### 🔹 Phase 2 – Project Generation

Generate the project **module by module**, starting with the **core module**.

---

## ♻️ For Refactoring an Existing Project

### 🔹 Phase 1 – Analysis (No Code Changes)

Analyze the current project and explain:

* Which parts comply with the instructions
* Which parts violate them
* Which modules should exist according to `AGENTS.md`

⚠️ **Do not generate code yet**.

---

### 🔹 Phase 2 – Refactor Plan

Propose a refactor plan composed of **small, ordered steps**.

Each step must be:

* **Atomic**
* **Reversible**
* Suitable for an **independent commit**

---

### 🔹 Phase 3 – Commit-Guided Refactor

For each step:

* Execute **only one step** of the plan
* Generate **only**:

  * Modified files
  * New files (if applicable)
* Do **not** touch anything else

✔️ This approach is ideal for quality control and clean pull requests.

---

## 💡 Tips

### ✅ Be Repetitive

Copilot does not mind repetition. Frequently remind it:

> "Follow strictly `copilot-instructions.md` and `AGENTS.md`."

---

### ✅ Force It to Stop When Needed

Include explicit instructions such as:

> "If there is any ambiguity, ask before continuing."

---

### ❌ Do Not Mix Tasks

Avoid asking Copilot to do multiple things at once.

❌ Do **not** combine:

* Refactoring
* Testing
* Migration

in a single request.

---

This workflow is intended to help teams avoid architectural drift and safely evolve Spring Boot projects using AI-assisted development.


