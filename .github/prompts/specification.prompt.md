---
agent: 'agent'
model: GPT-5.2
description: 'Write specifications for the Service. Ensure alignment with architecture and project instructions.'
tools: [read]
---

# Service Specification Prompt

## Purpose

Use this prompt to create clear, actionable specifications for new features, bug fixes, or technical debt in the Service. Specifications must enable developers and stakeholders to understand requirements, scope, and acceptance criteria before implementation begins. All specifications should adhere to the architectural principles in [architecture.instructions.md](../instructions/architecture.instructions.md), [project.instructions.md](../instructions/project.instructions.md), and [security.instructions.md](../instructions/security.instructions.md).
---

## Specification Template

### 1. Title
- Provide a concise, descriptive title for the feature or bug fix.

### 2. Description of the user story / task
- Briefly describe the background, motivation, or business need.
- Clearly state the problem to solve or the user story.
  - Example: "As a [user type], I want to [do something] so that [reason]."
- Reference related issues, tickets, or documentation if applicable.

### 3. Requirements
- List the functional and non-functional requirements.
- Be specific about what must be delivered.
- Reference modularity, extensibility, and local-first design where relevant.

### 4. Scope
- Define what is in scope and out of scope for this specification.

### 5. Documentation (design doc, runbooks, etc.) (optional)
- Add any relevant design considerations, diagrams, or links.
- Reference DDD, modularity, and separation of concerns as needed.

### 6. API Definition (optional)
- When applicable, provide API endpoints, and request/response examples.

### 7. Test Cases
- Define test cases to validate the implementation against the requirements.
- Include unit tests, integration tests, and end-to-end tests as applicable.
  - Unit test scenarios
  - Integration test scenarios
  - End-to-end test scenarios

### 8. Alerting & Monitoring Scenarios (optional)
- Define scenarios for alerting and monitoring to ensure reliability and performance.
- Include thresholds, expected behaviors, and response plans for incidents.

### 9. Acceptance Criteria
- Provide clear, testable criteria for completion.
- Use bullet points or Gherkin-style scenarios if helpful.

---

## Example

```
### Title
Add bulk upload for placement groups

### Description of the user story / task
Bulk upload is a frequently requested feature by operations teams to speed up onboarding.
As an admin, I want to upload multiple placement groups via CSV so that I can save time.

### Requirements
- Support CSV upload for placement groups
- Validate file format and data
- Show errors for invalid rows

### Scope
- In scope: UI, API, validation
- Out of scope: Export functionality

### Documentation (design doc, runbooks, etc.)
- See Figma design: [link]

### API Definition
- POST /placement-groups/bulk-upload
  - Request: CSV file
  - Response: 201 Created

### Test Cases
- Validate CSV upload endpoint
- Test error handling for invalid files
#### Unit test scenarios
- Test CSV parsing logic with valid and invalid inputs
#### Integration test scenarios
- Test end-to-end bulk upload flow with mock data
#### End-to-end test scenarios
- Simulate user uploading a CSV file and verify placement groups are created

### Alerting & Monitoring Scenarios
- Alert if bulk upload fails more than 3 times in an hour

### Acceptance Criteria
- Given a valid CSV, placement groups are created
- Invalid rows are reported with error messages
- UI shows upload progress
```

---

## Instructions

- Fill out each section above for your feature or bug fix.
- Review with stakeholders before implementation.
- Follow [architecture.instructions.md](../instructions/architecture.instructions.md), [project.instructions.md](../instructions/project.instructions.md), and [security.instructions.md](../instructions/security.instructions.md) for project overview and structure.

## Outcome:
A markdown document as `.workspace/specification/feature/{FEATURE_NAME}.md` that includes:
  - Title
  - Description of the user story / task
  - Requirements
  - Scope
  - Documentation (design doc, runbooks, etc.) (optional)
  - API Definition
  - Test Cases
      - Unit test scenarios
      - Integration test scenarios
      - End-to-end test scenarios
  - Alerting & Monitoring Scenarios (optional)
  - Acceptance Criteria
