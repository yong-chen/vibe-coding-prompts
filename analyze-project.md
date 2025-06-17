---
description: Ingest and Analyze a New Codebase
---

---
id: project-ingest-and-analyze
title: Ingest and Analyze a New Codebase
description: Understand a project's purpose, architecture, features, gaps, and readiness for future development. Designed for onboarding or project transitions.
input:
  - id: project_name
    label: Project Name
    type: string
    placeholder: e.g., MyApp, MyServices
  - id: project_summary
    label: Project Short Summary
    type: string
    placeholder: e.g., A full stack web app
  - id: base_path
    label: Relative Path to Codebase Root
    type: string
    placeholder: e.g., MyApp/
memory:
  persist: true
  tags: [{{project_name}}, codebase, analysis, onboarding]
---

## Goal

To guide an AI assistant in creating a detailed Project technical and architecture analysis using the code base in Markdown format, based on an initial user prompt. The document should be clear, aligh with code base, and suitable for a junior developer to understand and acting as traditional knowledge sharing from an expert of this project. Aiming to help developer or AI assistant for future work i.e. maintain, enhance, debug or implement new feature.

## Process

1.  **Receive Initial Prompt:** The user provides a brief description of this project.
2.  **Ask Clarifying Questions:** Before analyzing, the AI *must* ask clarifying questions to gather sufficient detail. The goal is to understand the base path of the code base and user's current understanding of this project. (This is not asking deep and comprehensive understanding, just capture what user knows now).
3.  **Generate Document:** Based on the initial prompt and the user's answers to the clarifying questions, generate a technical analysis document using the steps and structure outlined below.
4.  **Save Document:** Save the generated document as `[project_name]-analysis.md` inside the `{{base_path}}` directory.

## Clarifying Questions

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*   **Project Name:** "What is the project name? (e.g. MyApp, MyServices)" Remember the input in {{project_name}}
*   **Project Base Path:** "Relative path in the repo for this project? (e.g. MyApp/)" Remember the input in {{base_path}}
*   **Project Summary:** "What does this project provide?" remember the input in {{project_summary}}
*   **Tech Stack:"** "Can you provide general tech stack used (e.g. C#, .Net, web services, Azure function etc.)"
*   **Special concerns:** "Are there any special technical areas you want additional focus? (e.g. thread-safty, caching, resilience, performance)

## Steps
# Step 1: Ingest and Understand Codebase

Ingest the codebase located at:

```
{{base_path}}
```

Use the following summary as context:

{{project_summary}}

Begin by reviewing any available documentation files (`README.md`, `PROMPT.md`, `/docs`, etc.) and exploring the directory layout.

---

# Step 2: Analyze Application Structure

Perform a comprehensive walkthrough of the project:

- Backend and frontend architecture (if applicable)
- State management and data flow
- Frameworks, libraries, and internal tools
- Modular design and service boundaries
- Third-party dependencies

---

# Step 3: Document the Findings

Create a structured output with the following sections and export into a markdown file in the **{{base_path}}** :

## Project Purpose and Scope

Summarize what **{{project_name}}** is and what problem it solves. Reference the business domain or system context if available.

## Architecture Overview

Describe the technical architecture:

- High-level components and their relationships
- Patterns used (e.g., state-machine, microservices)
- How data flows through the system
- Key abstractions and their roles

## Key Features and Capabilities

List core functionality and services implemented by the codebase. Include any important integrations with external systems.

## Known Gaps or TODO Areas

Highlight areas needing improvement or completion:

- `TODO` and `FIXME` comments
- Dead code, stubs, or partial implementations
- Documentation gaps
- Areas of high complexity or tech debt

## Onboarding Tutorial

Write a short “How-To” section for new developers and export into a markdown file in the **{{base_path}}**:

- How to run/setup the project locally
- Where to start reading the code
- Common workflows
- Testing and debugging tips

## Recommendations for Next Steps

Provide engineering suggestions:

- Architectural improvements
- Code cleanup opportunities
- Places ready for feature expansion
- Dependencies worth updating

---

# Step 4: Save to Windsurf Cascade Memories

Store your structured findings into **Windsurf Cascade Memories** with the following tag:

```
{{project_name}}-ingest
```

This enables persistent reference and save in memories in future sessions.

---

# Step 5: Confirm Completion

Once memory is saved, confirm the following:

✅ Codebase successfully ingested  
✅ Findings summarized and saved to memory as `{{project_name}}-ingest`  
✅ Ready to receive next prompt or workflow

Prompt user:

**“Project analysis complete and saved to memory. Ready for next instruction.”**