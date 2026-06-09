# Project Pulse Implementation Plan

## Summary

Build a lightweight dashboard frontend for Mona's Project Pulse by creating a static app under `app/` and a VS Code launch configuration. The dashboard will display project status cards using `app/project-data.json`, styled with `app/styles.css`, and rendered through `app/index.html`.

## File ownership and responsibilities

- `app/index.html`
  - Owner: Coder
  - Responsibility: Build the dashboard structure, wire in project data, and include references to styles and data.

- `app/styles.css`
  - Owner: Designer
  - Responsibility: Define visual layout, responsive cards, status badges, typography, spacing, and accessible color contrast.

- `app/project-data.json`
  - Owner: Coder
  - Responsibility: Provide example dashboard data for Project Pulse, including project name, status, priority, owner, and progress.

- `.vscode/launch.json`
  - Owner: Coder
  - Responsibility: Configure a deterministic Codespace launch that serves the dashboard from `app/`, opening `index.html`.

- `docs/project-pulse-plan.md`
  - Owner: Planner
  - Responsibility: Document the implementation plan, including dependencies, parallel work decisions, and validation expectations.

## Implementation steps

1. Create `app/project-data.json`
   - Define a small set of sample project records.
   - Include fields for title, status, priority, owner, due date, progress, and summary.
   - Use JSON only, no script or dynamic data injection.

2. Create `app/index.html`
   - Add a static HTML page that loads `project-data.json` using JavaScript.
   - Render a dashboard header, project cards, and status semantics.
   - Reference `styles.css` and include minimal client-side script.
   - Keep markup structured for accessibility.

3. Create `app/styles.css`
   - Add dashboard layout rules, card styles, badge styles, and responsive behavior.
   - Ensure readable typography, spacing, and a polished UI.
   - Use CSS class names like `.dashboard`, `.project-card`, `.status-badge`, and `.priority-label`.

4. Create `.vscode/launch.json`
   - Configure a launch profile that launches a static server or opens `index.html` in the workspace.
   - Set `cwd` to `${workspaceFolder}/app`.
   - Use deterministic values so the dashboard is easy to preview.

## Dependencies

- `app/index.html` depends on `app/project-data.json` for the sample dashboard content.
- `app/index.html` depends on `app/styles.css` for layout and presentation.
- `.vscode/launch.json` depends on the app folder structure existing and `index.html` being the entrypoint.

## Parallel work decisions

- `app/styles.css` can be worked on in parallel with `app/project-data.json` because styling does not depend on the final JSON contents beyond expected field names.
- `app/index.html` should be completed after `app/project-data.json` is defined, since it reads the JSON schema and renders the cards.
- `.vscode/launch.json` can be created in parallel with `app/styles.css` and `app/project-data.json` because it only depends on the app directory layout.

## Validation expectations

- `app/index.html` loads successfully in a browser or Codespace preview without JavaScript errors.
- The dashboard renders at least three project cards from `app/project-data.json`.
- Status badges and priority labels are visually distinct.
- The layout responds to narrow and wide screen widths.
- `.vscode/launch.json` opens the app from `app/` and targets `index.html` rather than a directory listing.
- The plan file documents responsibilities, dependencies, parallel work decisions, and expected validation checks.

## Edge cases and notes

- If the Codespace preview cannot serve `index.html` directly, use a simple static server configuration in `.vscode/launch.json` that points to `app/`.
- Keep the data file simple; avoid external API calls or runtime dependencies.
- Ensure the UI is accessible and readable without relying on custom fonts.

## Open questions

- Should the dashboard include any interactive filtering or search controls, or remain a static status board for the first implementation?
- Does Mona prefer a specific color palette or brand tone for Project Pulse, or should the designer choose a polished neutral style?
