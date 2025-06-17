---
description: Conduct a thorough code review
---

---
description: Conduct a thorough code review
---

---
id: code-review
title: Conduct a thorough code review
description: Perform a detailed review not just of the changed code, but also in the context of the entire codebase. Leverage existing documentation and issue descriptions to validate completeness, performance, test coverage, and release readiness
input:
  - id: project_name
    label: Project Name
    type: string
    placeholder: e.g., MyApp, MyServices
  - id: issue_name
    label: Issue
    type: string
    placeholder: e.g., Jira number WEB-12345
  - id: issue_summary
    label: Issue
    type: string
    placeholder: e.g., brief summary of the issue or feature or bug
  - id: base_path
    label: Relative Path to Codebase Root
    type: string
    placeholder: e.g., server/services/
  - id: branch_name
    label: Repo branch name
    type: string
    placeholder: e.g., feature-WEB-12345
memory:
  persist: false
---

## Goal

Use Cascade memories and project documentation to understand the issue (feature, bug, or task) using the provided context. Conduct a review of all code changes in the specified branch and assess them in the broader context of the project.

Review objectives:

- Understand the ask defined in the issue (jira story)
- Determine whether the fix addresses the issue, acceptance criteria
- Identify any risks of performance degradation (e.g., thread safety, memory, algorithmic complexity)
- Evaluate unit test coverage and gaps
- Spot any critical blockers that may prevent a release PR

## Process

1. Receive Initial Input – Collect metadata: project, issue, branch, base path
2. Ask Clarifying Questions – If needed, gather additional context before review
3. Analyze Codebase and Branch Changes – Evaluate code and documentation comprehensively
4. Generate Review Document – Output detailed code review
5. Confirm Completion – Ensure outcomes are saved and user notified

## Clarifying Questions (Examples)

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*   **Project Name:** "What is the project name? (e.g. Web services, Admin Console)" Remember the input in {{project_name}}
*   **Project Base Path:** "Relative path in the mono repo for this project? (e.g. server\services)" Remember the input in {{base_path}}
*   **Issue Name:** "Jira ID" Remember the input in {{issue_name}}
*   **Issue Summary:** "What is the issue about?" remember the input in {{issue_summary}}
*   **Branch Name:"** "Rep branch name" remember the input in {{branch_name}}
*   **Special concerns:** "Are there any special technical area you want additional focus? (e.g. thread-safty, caching, resilience, performance)

## Steps
# Step 1: Ingest Context and Code Changes
- Navigate to the codebase at {{base_path}}
- Review relevant documentation (README.md, PROMPT.md, /docs, etc.)
- Search Cascade memories relevant to {{project_name}}
- Use Git commands to list and extract all changes in {{branch_name}}

---

# Step 2: Review Code in Context

Conduct a thorough review with attention to:
- Issue alignment – Does the change solve the stated problem?
- Code quality – Is the code clear, maintainable, idiomatic?
- Performance – Any inefficiencies or regression risks?
- Test coverage – Do the changes have sufficient tests? Are they meaningful?
- Security – Any vulnerabilities introduced?
- Release readiness – Any critical blockers for PR approval?

---

# Step 3: Document Review Findings

Output a structured Markdown file saved to {{base_path}}:

- Include: file paths, code references with line numbers
- Provide: estimated unit test coverage
- Add: recommendations categorized as:
✅ Ready for Pull Request
⚠️ Requires fixes before merge
❌ Does not adequately address issue

---


# Step 4: Confirm Completion

Ensure the following:
- Code review output saved as {{issue_name}}-code-review.md
- Summary persisted as memory entry: {{branch_name}}-code-review
- Notify user: "Code review completed. Ready for next instruction."