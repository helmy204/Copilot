---
agent: agent
model: Claude Sonnet 4.6 (copilot)
description: Write BDD tests for the API feature. Follow the Reqnroll/Gherkin layered architecture. Ensure all tests pass and code coverage is above 85%. Document the testing process and results.
tools: [
  'search/codebase', 'search/usages', 'edit/editFiles','search/searchResults', 'search/changes', 'vscode/openSimpleBrowser', 'search',
  'execute/getTerminalOutput', 'execute/runInTerminal', 'read/terminalLastCommand', 'read/terminalSelection', 'execute/createAndRunTask', 'execute/getTaskOutput', 'execute/runTask', 'execute/runTests', 
  'vscode/extensions', 'read/terminalLastCommand', 'read/terminalSelection', 'vscode/vscodeAPI'
  'web/githubRepo', 'vscode/getProjectSetupInfo', 'vscode/installExtension', 'vscode/newWorkspace', 'vscode/runCommand', 'web/fetch', 
  'read/problems', 'execute/testFailure'
  ]
---
# Write BDD tests

## Instructions:
- DO NOT change existing code outside of the following folder paths [`**/*.Specs`].
- Follow ([copilot instructions](../instructions/copilot.instructions.md)) for agent behavior.
- Follow ([project instructions](../instructions/project.instructions.md)) for project overview and structure.
- Follow ([architecture instructions](../instructions/architecture.instructions.md)) for architecture guidelines.
- Follow ([gherkin instructions](../instructions/gherkin.instructions.md)) for testing guidelines.

## Task:
- Read the test plan attached as reference (`/.github/features/{FEATURE_NAME}/Plan.md`). `{FEATURE_NAME}` is the name of the feature you are working on and will be provided as a reference.
- Write BDD test cases for the feature iteratively in the appropriate subfolder under `/**/*.Specs` (e.g., `/src/*.Specs/*Tests.cs`, etc.).
- Iteratively run & fix all the test cases until the success rate is 100%.
- Iteratively run & fix the test cases until code coverage is more than 85%.
- Run the full test suite to ensure existing functionality is not broken.
- Document any changes made to the tests, including new files, modified files, and any assumptions or limitations encountered during implementation.

## Outcome:
- Test summary in a markdown file `.workspace/test/{FEATURE_NAME}_summary.md` that includes:
  - Number of test cases written
  - Number of test cases passed
  - Number of test cases failed
  - Code coverage percentage
- A markdown document as `.workspace/test/{FEATURE_NAME}_summary.md` that includes:
  - Overview of the feature and its purpose
  - List of test files changed or added
  - Testing results and any issues encountered
  - Any assumptions or limitations identified during the implementation phase