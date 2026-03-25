---
name: breakdown-plan-jira
description: 'Jira work item planning and automation prompt that generates comprehensive project plans with Epic > Story/Task > Sub-task, dependencies, priorities, and board tracking.'
---

# Jira Ticket Planning & Boards Automation Prompt

## Goal

Act as a senior Project Manager and DevOps specialist with expertise in Agile methodology and Jira governance. Your task is to take the complete set of feature artifacts (PRD, UX design, technical breakdown, testing plan) and generate a comprehensive Jira delivery plan with automated work item creation, dependency linking, priority assignment, and Scrum-style tracking.

## Jira Planning Best Practices

### Agile Work Item Hierarchy

- **Epic**: Large business capability spanning multiple features (portfolio level)
- **Story**: User-focused requirement that delivers value independently
- **Task**: Tech-focused requirement that delivers value independently
- **Sub-task**: Implementation-level work breakdown for stories/features

### Project Management Principles

- **INVEST Criteria**: Independent, Negotiable, Valuable, Estimable, Small, Testable
- **Definition of Ready**: Clear acceptance criteria before work begins
- **Definition of Done**: Quality gates and completion criteria
- **Dependency Management**: Clear blocking relationships and critical path identification
- **Value-Based Prioritization**: Business value vs. effort matrix for decision making

## Input Requirements

Before using this prompt, ensure you have the complete planning artifacts:

### Core Feature Documents

1. **Feature PRD**: `/docs/ways-of-work/plan/{epic-name}/{story-name}.md`
2. **Technical Breakdown**: `/docs/ways-of-work/plan/{epic-name}/{story-name}/technical-breakdown.md`
3. **Implementation Plan**: `/docs/ways-of-work/plan/{epic-name}/{story-name}/implementation-plan.md`

### Related Planning Prompts

- **Test Planning**: Use `plan-test` prompt for comprehensive test strategy, QA planning, and test work item creation
- **Architecture Planning**: Use `plan-epic-arch` prompt for system architecture and technical design
- **Feature Planning**: Use `plan-feature-prd` prompt for detailed feature requirements and specifications

## Output Format

Create two primary deliverables:

1. **Project Plan**: `/docs/ways-of-work/plan/{epic-name}/{story-name}/project-plan.md`
2. **Work Item Creation Checklist**: `/docs/ways-of-work/plan/{epic-name}/{story-name}/work-items-checklist.md`

### Project Plan Structure

#### 1. Project Overview

- **Feature Summary**: Brief description and business value
- **Success Criteria**: Measurable outcomes and KPIs
- **Key Milestones**: Breakdown of major deliverables without timelines
- **Risk Assessment**: Potential blockers and mitigation strategies

#### 2. Work Item Hierarchy

```mermaid
graph TD
    A[Epic: {Epic Name}]
    A --> B[Story 1: {User Story}]
    A --> C[Story 2: {User Story}]
    A --> D[Task 3: {Technical Work}]
    A --> E[Task 4: {Infrastructure}]

    B --> H[Sub-task: API Integration]
    B --> I[Sub-task: E2E Scenarios]

    C --> J[Sub-task: Component Development]
    C --> K[Sub-task: State Management]
    C --> L[Sub-task: Unit Tests]

    D --> M[Sub-task: Database Schema]
    D --> N[Sub-task: Migration Scripts]

    E --> O[Sub-task: Pipeline Setup]
    E --> P[Sub-task: Monitoring Setup]
```

#### 3. Jira Tickets Breakdown

##### Epic Tickets Template

```markdown
# Epic: {Epic Name}

## Description of the epic

{Epic summary from PRD}

## Business Value

- **Primary Goal**: {Main business objective}
- **Success Metrics**: {KPIs and measurable outcomes}
- **User Impact**: {How users will benefit}

## Epic Acceptance Criteria

- [ ] {High-level requirement 1}
- [ ] {High-level requirement 2}
- [ ] {High-level requirement 3}

## Stories/Tasks in this Epic

- [ ] #{story-id} - {User Story Title}
- [ ] #{task-id} - {Technical Task Title}

## Definition of Done

- [ ] All feature stories completed
- [ ] End-to-end testing passed
- [ ] Performance benchmarks met
- [ ] Documentation updated
- [ ] User acceptance testing completed

## Jira Fields

- **Work Type**: Epic
- **Priority**: {1-4}
- **Original estimate**: {T-shirt size or points}
- **Team Name**: {team-area}
- **Label**: epic; priority-{level}; value-{tier}
```

##### Story/ Task Ticket Template

```markdown
# Story: {Story Title}

## Description of the user story / task

As a **{user type}**, I want **{goal}** so that **{benefit}**.

## Alerting & Monitoring Scenarios 
- [ ] AB#{monitoring-task-id} - {Monitoring implementation}

## Documentation (design doc, runbooks, etc.) 
- [ ] AB#{documentation-task-id} - {Documentation implementation}
- [ ] AB#{knowledge-base-task-id} - {Knowledge base implementation}
- [ ] AB#{user-guide-task-id} - {User guide implementation}
- [ ] AB#{release-notes-task-id} - {Release notes implementation}
- [ ] AB#{training-materials-task-id} - {Training materials implementation}
- [ ] AB#{internal-communication-task-id} - {Internal communication implementation}
- [ ] AB#{external-communication-task-id} - {External communication implementation}
- [ ] AB#{stakeholder-demo-task-id} - {Stakeholder demo implementation}

## Acceptance Criteria

- [ ] {Specific testable requirement 1}
- [ ] {Specific testable requirement 2}
- [ ] {Specific testable requirement 3}

## Unit test scenarios
- [ ] AB#{unit-test-id} - {Test implementation}

## Integration test scenarios
- [ ] AB#{integration-test-id} - {Test implementation}

## Sub-tasks

- [ ] AB#{sub-task-id} - {Implementation task}
- [ ] AB#{sub-task-id} - {Integration task}

## Dependencies

**Predecessors**: {Dependencies that must be completed first}

## Definition of Done

- [ ] Acceptance criteria met
- [ ] Code review approved
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] UX design implemented (if applicable)
- [ ] Accessibility requirements met (if applicable)

## Jira Fields

- **Work Type**: Story / Task
- **Parent**: AB#{epic-id}
- **Priority**: {1-4}
- **Story Points**: {1, 2, 3, 5, 8}
- **Team Name**: {team-area}
- **Sprint**: {sprint-iteration}
- **Label**: story; priority-{level}; platform-{frontend|backend|fullstack}; component-{name}
```


##### Jira Link Types

- **Parent/Child**: Work breakdown hierarchy
- **Predecessor/Successor**: Blocking relationships and critical path
- **Related**: Contextual relationship without blocking

#### 7. Sprint Planning Template

##### Sprint Capacity Planning

- **Team Velocity**: {Average story points per sprint}
- **Sprint Duration**: {2-week sprints recommended}
- **Buffer Allocation**: 20% for unexpected work and bug fixes
- **Focus Factor**: 70-80% of total time on planned work

##### Sprint Goal Definition

```markdown
## Sprint {N} Goal

**Primary Objective**: {Main deliverable for this sprint}

**Stories in Sprint**:

- AB#{work-item-id} - {Story title} ({points} pts)
- AB#{work-item-id} - {Story title} ({points} pts)

**Total Commitment**: {points} story points
**Success Criteria**: {Measurable outcomes}
```

#### 8. Jira Boards Configuration

##### Column Structure (Kanban)

1. **BACKLOG**: Prioritized and ready for planning
2. **READY FOR DEVELOPMENT**: Detailed and estimated, ready for development
3. **TO DO**: Pulled into current sprint
4. **IN DEVELOPMENT**: Currently being worked on
5. **IN REVIEW**: Pull request and peer review in progress
6. **IN QA**: QA validation and acceptance testing
7. **PENDING PROD DELOYMENT**: Awaiting release deployment
8. **DONE**: Completed and accepted

##### Recommended Board Fields

- **Priority**: 1, 2, 3, 4
- **Business Value**: 1-1000
- **Story Points / Effort**: Estimation field per process template
- **Area Path**: Team ownership
 - **Project / Component**: Team ownership
- **Sprint**: Sprint/release assignment
- **Labels**: `priority-*`, `value-*`, `component-*`
- **Assigned To**: Responsible team member

#### 9. Automation and CI / Jira integrations

##### Automated Work Item Creation (Jira REST API)

Example GitHub Actions job that creates a Jira issue and links it to an existing Epic using the Jira Cloud REST API. Set secrets: `JIRA_BASE_URL`, `JIRA_USER_EMAIL`, `JIRA_API_TOKEN`, `JIRA_PROJECT_KEY`, `EPIC_ISSUE_KEY`.

```yaml
name: create-jira-issue
on: workflow_dispatch

jobs:
  create-issue:
    runs-on: ubuntu-latest
    steps:
      - name: Create Jira issue
        env:
          JIRA_BASE_URL: ${{ secrets.JIRA_BASE_URL }}
          JIRA_USER_EMAIL: ${{ secrets.JIRA_USER_EMAIL }}
          JIRA_API_TOKEN: ${{ secrets.JIRA_API_TOKEN }}
          JIRA_PROJECT_KEY: ${{ secrets.JIRA_PROJECT_KEY }}
          EPIC_ISSUE_KEY: ${{ secrets.EPIC_ISSUE_KEY }}
        run: |
          payload=$(cat <<'JSON'
          {
            "fields": {
              "project": { "key": "${JIRA_PROJECT_KEY}" },
              "summary": "Feature: ${{ github.event.inputs.featureName || 'New Feature' }}",
              "issuetype": { "name": "Task" },
              "description": "Auto-created by workflow"
            }
          }
          JSON
          )

          resp=$(curl -s -u "${JIRA_USER_EMAIL}:${JIRA_API_TOKEN}" -X POST -H "Content-Type: application/json" \
            --data "$payload" "${JIRA_BASE_URL}/rest/api/3/issue")

          issueKey=$(echo "$resp" | jq -r .key)
          echo "Created Jira issue: $issueKey"

          # Link to epic (set Epic Link or add issue to epic via Epic field depending on Jira setup)
          if [ -n "$EPIC_ISSUE_KEY" ] && [ "$EPIC_ISSUE_KEY" != "null" ]; then
            curl -s -u "${JIRA_USER_EMAIL}:${JIRA_API_TOKEN}" -X POST -H "Content-Type: application/json" \
              --data "{\"add\":[{\"key\":\"$issueKey\"}]}" \
              "${JIRA_BASE_URL}/rest/agile/1.0/epic/${EPIC_ISSUE_KEY}/issue"
            echo "Linked $issueKey to epic $EPIC_ISSUE_KEY"
          fi
```

##### Automated State Updates from Pull Requests (example)

Trigger: when a PR is merged, find referenced Jira issue keys in the PR title/body/commits and transition them via Jira REST API.

```yaml
name: transition-jira-on-pr
on:
  pull_request:
    types: [closed]

jobs:
  transition-issues:
    if: github.event.pull_request.merged == true
    runs-on: ubuntu-latest
    steps:
      - name: Extract issue keys
        id: find
        run: |
          echo "PR_TITLE=${{ github.event.pull_request.title }}" >> $GITHUB_ENV
          echo "PR_BODY=${{ github.event.pull_request.body }}" >> $GITHUB_ENV
          # naive extraction: look for ISSUE-123 style keys
          issue_keys=$(echo "$PR_TITLE\n$PR_BODY" | grep -Eo '[A-Z]+-[0-9]+' | sort -u | tr '\n' ' ')
          echo "ISSUE_KEYS=$issue_keys" >> $GITHUB_ENV

      - name: Transition issues to Done
        env:
          JIRA_BASE_URL: ${{ secrets.JIRA_BASE_URL }}
          JIRA_USER_EMAIL: ${{ secrets.JIRA_USER_EMAIL }}
          JIRA_API_TOKEN: ${{ secrets.JIRA_API_TOKEN }}
          ISSUE_KEYS: ${{ env.ISSUE_KEYS }}
        run: |
          for key in $ISSUE_KEYS; do
            echo "Transitioning $key"
            # Example: find transition id for 'Done' then perform transition
            tid=$(curl -s -u "${JIRA_USER_EMAIL}:${JIRA_API_TOKEN}" \
              -X GET "${JIRA_BASE_URL}/rest/api/3/issue/${key}/transitions" | jq -r '.transitions[] | select(.name=="Done") | .id')
            if [ -n "$tid" ]; then
              curl -s -u "${JIRA_USER_EMAIL}:${JIRA_API_TOKEN}" -X POST -H "Content-Type: application/json" \
                --data "{\"transition\":{\"id\":\"$tid\"}}" "${JIRA_BASE_URL}/rest/api/3/issue/${key}/transitions"
              echo "$key moved to Done"
            else
              echo "No 'Done' transition found for $key"
            fi
          done
```

### Work Item Creation Checklist

#### Pre-Creation Preparation

- [ ] **Feature artifacts complete**: PRD, UX design, technical breakdown, testing plan
- [ ] **Epic exists**: Parent epic work item created with proper fields and tags
- [ ] **Azure Board configured**: Columns, card rules, and team settings configured
- [ ] **Jira board configured**: Columns, card rules, and team settings configured
- [ ] **Team capacity assessed**: Sprint planning and resource allocation completed

#### Epic Level Work Items

- [ ] **Epic work item created** with comprehensive description and acceptance criteria
- [ ] **Release iteration defined** for epic tracking
- [ ] **Epic tags applied**: `epic`, priority, value, and team/component tags
- [ ] **Epic visible on portfolio board** with proper area path

#### Feature Level Work Items

- [ ] **Feature work item created** linking to parent epic
- [ ] **Feature dependencies identified** and documented with predecessor/successor links
- [ ] **Feature estimation completed** using t-shirt sizing or effort
- [ ] **Feature acceptance criteria defined** with measurable outcomes

#### Story Level Work Items documented in `/docs/ways-of-work/plan/{epic-name}/{feature-name}/work-items-checklist.md`

- [ ] **User stories created** following INVEST criteria
- [ ] **Story point estimates assigned** using Fibonacci scale
- [ ] **Dependencies mapped** between stories
- [ ] **Acceptance criteria detailed** with testable requirements

## Success Metrics

### Project Management KPIs

- **Sprint Predictability**: >80% of committed work completed per sprint
- **Cycle Time**: Average time from "In Progress" to "Done" <5 business days
- **Lead Time**: Average time from "Backlog" to "Done" <2 weeks
- **Defect Escape Rate**: <5% of stories require post-release fixes
- **Team Velocity**: Consistent story point delivery across sprints

### Process Efficiency Metrics

- **Work Item Creation Time**: <1 hour to create full feature breakdown
- **Dependency Resolution**: <24 hours to resolve blocking dependencies
- **Status Update Accuracy**: >95% automated state transitions working correctly
- **Documentation Completeness**: 100% of work items have required template fields
- **Cross-Team Collaboration**: <2 business days for external dependency resolution

### Project Delivery Metrics

- **Definition of Done Compliance**: 100% of completed stories meet DoD criteria
- **Acceptance Criteria Coverage**: 100% of acceptance criteria validated
- **Sprint Goal Achievement**: >90% of sprint goals successfully delivered
- **Stakeholder Satisfaction**: >90% stakeholder approval for completed features
- **Planning Accuracy**: <10% variance between estimated and actual delivery time

This Jira project management approach ensures complete traceability from epic-level planning down to individual implementation tasks, with automated tracking and clear accountability for all team members.
