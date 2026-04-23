---
agent: 'agent'
model: 'Claude Sonnet 4.5'
tools: [
  'search/codebase', 'search/usages', 'edit/editFiles','search/searchResults', 'search/changes', 'vscode/openSimpleBrowser', 'search',
  'execute/getTerminalOutput', 'execute/runInTerminal', 'read/terminalLastCommand', 'read/terminalSelection', 'execute/createAndRunTask', 'execute/getTaskOutput', 'execute/runTask', 'execute/runTests', 
  'vscode/extensions', 'read/terminalLastCommand', 'read/terminalSelection', 'vscode/vscodeAPI'
  'web/githubRepo', 'vscode/getProjectSetupInfo', 'vscode/installExtension', 'vscode/newWorkspace', 'vscode/runCommand', 'web/fetch', 
  'read/problems', 'execute/testFailure'
  ]
description: 'Implement a given feature for a given service.'
---

## Instructions:
- Follow [copilot](../instructions/copilot.instructions.md) for agent behavior.
- Follow [project](../instructions/project.instructions.md) for project overview and structure.
- Follow [architecture](../instructions/architecture.instructions.md) for architecture guidelines.
- Follow [coding c#](../instructions/coding-csharp.instructions.md) for C# coding standards.
- Follow [coding sql](../instructions/coding-sql.instructions.md) for SQL coding standards.
- Follow [testing](../instructions/testing.instructions.md) for testing guidelines.

## Task:
- Read the implementation plan attached as reference (`.github/features/{FEATURE_NAME}/Plan.md`. `{FEATURE_NAME}` is the name of the feature you are working on and it will be given with prompt as a reference.
- Read the implementation steps from the plan and implement the feature iteratively in `api/` folder.
- Ensure the feature is modular, maintainable, and follows the project standards.
- Document any changes made to the codebase, including new files, modified files, and any assumptions or limitations encountered during implementation.

## Outcome:
- Given feature is implemented successfully.
- A markdown document as `api/.workspace/feature/{FEATURE_NAME}.md` that includes:
  - Overview of the feature and its purpose
  - List of files changed or added
  - Any assumptions or limitations identified during the implementation phase