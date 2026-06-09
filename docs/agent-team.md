# Agent team

This project uses a custom agent team defined under `.github/agents` to build Mona's Project Pulse dashboard. The work is orchestrated from a GitHub Codespace using GitHub Copilot CLI.

- **Planner**
  - Model: Claude Opus 4.7 (copilot)
  - Responsibility: Research the repository, inspect relevant files, identify dependencies and edge cases, and produce a practical implementation plan.
  - Definition: `.github/agents/planner.agent.md`

- **Coder**
  - Model: GPT-5.5 (copilot)
  - Responsibility: Implement code changes, write or update files, follow repository patterns, and validate changes within the assigned file scope.
  - Definition: `.github/agents/coder.agent.md`

- **Designer**
  - Model: Gemini 3.1 Pro (copilot)
  - Responsibility: Create the dashboard UI/UX, style the interface, ensure clear information hierarchy, and make the frontend visually polished and accessible.
  - Definition: `.github/agents/designer.agent.md`

- **Orchestrator**
  - Model: Claude Opus 4.7 (copilot)
  - Responsibility: Coordinate Planner, Coder, and Designer work, assign file scopes, manage dependencies, and ensure the integrated Project Pulse dashboard is delivered consistently.
  - Definition: `.github/agents/orchestrator.agent.md`
