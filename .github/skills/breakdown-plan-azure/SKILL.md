---
name: breakdown-plan-azure
description: 'Azure DevOps work item planning and automation prompt that generates comprehensive project plans with Epic > Feature > Story > Test hierarchy, dependencies, priorities, and board tracking.'
---

# Azure DevOps Work Item Planning & Boards Automation Prompt

## Goal

Act as a senior Project Manager and DevOps specialist with expertise in Agile methodology and Azure Boards governance. Your task is to take the complete set of feature artifacts (PRD, UX design, technical breakdown, testing plan) and generate a comprehensive Azure DevOps delivery plan with automated work item creation, dependency linking, priority assignment, and Kanban-style tracking.

## Azure DevOps Planning Best Practices

### Agile Work Item Hierarchy

- **Epic**: Large business capability spanning multiple features (portfolio level)
- **Feature**: Deliverable user-facing functionality within an epic
- **User Story**: User-focused requirement that delivers value independently
- **Test Case/Test Task**: Quality assurance work for validating stories and features
- **Task**: Implementation-level work breakdown for stories/features

### Project Management Principles

- **INVEST Criteria**: Independent, Negotiable, Valuable, Estimable, Small, Testable
- **Definition of Ready**: Clear acceptance criteria before work begins
- **Definition of Done**: Quality gates and completion criteria
- **Dependency Management**: Clear blocking relationships and critical path identification
- **Value-Based Prioritization**: Business value vs. effort matrix for decision making

## Input Requirements

Before using this prompt, ensure you have the complete planning artifacts:

### Core Feature Documents

1. **Feature PRD**: `/docs/ways-of-work/plan/{epic-name}/{feature-name}.md`
2. **Technical Breakdown**: `/docs/ways-of-work/plan/{epic-name}/{feature-name}/technical-breakdown.md`
3. **Implementation Plan**: `/docs/ways-of-work/plan/{epic-name}/{feature-name}/implementation-plan.md`

### Related Planning Prompts

- **Test Planning**: Use `plan-test` prompt for comprehensive test strategy, QA planning, and test work item creation
- **Architecture Planning**: Use `plan-epic-arch` prompt for system architecture and technical design
- **Feature Planning**: Use `plan-feature-prd` prompt for detailed feature requirements and specifications

## Output Format

Create two primary deliverables:

1. **Project Plan**: `/docs/ways-of-work/plan/{epic-name}/{feature-name}/project-plan.md`
2. **Work Item Creation Checklist**: `/docs/ways-of-work/plan/{epic-name}/{feature-name}/work-items-checklist.md`

### Project Plan Structure

#### 1. Project Overview

- **Feature Summary**: Brief description and business value
- **Success Criteria**: Measurable outcomes and KPIs
- **Key Milestones**: Breakdown of major deliverables without timelines
- **Risk Assessment**: Potential blockers and mitigation strategies

#### 2. Work Item Hierarchy

```mermaid
graph TD
    A[Epic: {Epic Name}] --> B[Feature: {Feature Name}]
    B --> C[User Story 1: {User Story}]
    B --> D[User Story 2: {User Story}]
    B --> E[User Story 3: {Technical Work}]
    B --> F[User Story 4: {Infrastructure}]

    C --> G[Task: Frontend Implementation]
    C --> H[Task: API Integration]
    C --> I[Test Task: E2E Scenarios]

    D --> J[Task: Component Development]
    D --> K[Task: State Management]
    D --> L[Test Task: Unit Tests]

    E --> M[Task: Database Schema]
    E --> N[Task: Migration Scripts]

    F --> O[Task: Pipeline Setup]
    F --> P[Task: Monitoring Setup]
```

#### 3. Azure DevOps Work Items Breakdown

##### Epic Work Item Template

```markdown
# Epic: {Epic Name}

## Epic Description

{Epic summary from PRD}

## Business Value

- **Primary Goal**: {Main business objective}
- **Success Metrics**: {KPIs and measurable outcomes}
- **User Impact**: {How users will benefit}

## Epic Acceptance Criteria

- [ ] {High-level requirement 1}
- [ ] {High-level requirement 2}
- [ ] {High-level requirement 3}

## Features in this Epic

- [ ] #{feature-id} - {Feature Name}

## Definition of Done

- [ ] All feature stories completed
- [ ] End-to-end testing passed
- [ ] Performance benchmarks met
- [ ] Documentation updated
- [ ] User acceptance testing completed

## Azure DevOps Fields

- **Work Item Type**: Epic
- **Priority**: {1-4}
- **Business Value**: {1-1000}
- **Effort**: {T-shirt size or points}
- **Area Path**: {team-area}
- **Iteration Path**: {release-iteration}
- **Tags**: epic; priority-{level}; value-{tier}
```

##### Feature Work Item Template

```markdown
# Feature: {Feature Name}

## Feature Description

{Feature summary from PRD}

## User Stories in this Feature

- [ ] #{story-id} - {User Story Title}
- [ ] #{story-id} - {User Story Title}

## Dependencies

**Successor to**: {Work items this feature blocks}
**Predecessor of**: {Work items blocking this feature}

## Acceptance Criteria

- [ ] {Feature-level requirement 1}
- [ ] {Feature-level requirement 2}

## Definition of Done

- [ ] All user stories delivered
- [ ] Integration testing passed
- [ ] UX review approved
- [ ] Performance testing completed

## Azure DevOps Fields

- **Work Item Type**: Feature
- **Parent**: AB#{epic-id}
- **Priority**: {1-4}
- **Business Value**: {1-1000}
- **Effort**: {Points or t-shirt size}
- **Area Path**: {team-area}
- **Iteration Path**: {release-iteration}
- **Tags**: feature; priority-{level}; value-{tier}; component-{name}
```

##### User Story Work Item Template

```markdown
# User Story: {Story Title}

## Story Statement

As a **{user type}**, I want **{goal}** so that **{benefit}**.

## Acceptance Criteria

- [ ] {Specific testable requirement 1}
- [ ] {Specific testable requirement 2}
- [ ] {Specific testable requirement 3}

## Child Tasks

- [ ] AB#{task-id} - {Implementation task}
- [ ] AB#{task-id} - {Integration task}

## Testing Requirements

- [ ] AB#{test-id} - {Test implementation}

## Dependencies

**Predecessors**: {Dependencies that must be completed first}

## Definition of Done

- [ ] Acceptance criteria met
- [ ] Code review approved
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] UX design implemented
- [ ] Accessibility requirements met

## Azure DevOps Fields

- **Work Item Type**: User Story
- **Parent**: AB#{feature-id}
- **Priority**: {1-4}
- **Business Value**: {1-1000}
- **Story Points**: {1, 2, 3, 5, 8}
- **Area Path**: {team-area}
- **Iteration Path**: {sprint-iteration}
- **Tags**: user-story; priority-{level}; platform-{frontend|backend|fullstack}; component-{name}
```


##### Azure DevOps Link Types

- **Parent/Child**: Work breakdown hierarchy
- **Predecessor/Successor**: Blocking relationships and critical path
- **Related**: Contextual relationship without blocking
- **Tests/Tested By**: Validation linkage between stories and test assets

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

#### 8. Azure Boards Configuration

##### Column Structure (Kanban)

1. **Backlog**: Prioritized and ready for planning
2. **Approved**: Detailed and estimated, ready for development
3. **Committed**: Pulled into current sprint
4. **In Progress**: Currently being worked on
5. **Code Review**: Pull request and peer review in progress
6. **Testing**: QA validation and acceptance testing
7. **Done**: Completed and accepted

##### Recommended Board Fields

- **Priority**: 1, 2, 3, 4
- **Business Value**: 1-1000
- **Story Points / Effort**: Estimation field per process template
- **Area Path**: Team ownership
- **Iteration Path**: Sprint/release assignment
- **Tags**: `priority-*`, `value-*`, `component-*`
- **Assigned To**: Responsible team member

#### 9. Automation and Azure Pipelines

##### Automated Work Item Creation

```yaml
trigger: none
pr: none

parameters:
- name: featureName
  type: string
- name: epicId
  type: string

pool:
  vmImage: ubuntu-latest

steps:
- task: AzureCLI@2
  displayName: Create feature work item
  inputs:
    scriptType: bash
    scriptLocation: inlineScript
    inlineScript: |
      az extension add --name azure-devops --only-show-errors
      az devops configure --defaults organization="$(ADO_ORG_URL)" project="$(ADO_PROJECT)"

      feature_id=$(az boards work-item create \
        --type "Feature" \
        --title "Feature: ${{ parameters.featureName }}" \
        --fields "System.AreaPath=$(ADO_AREA_PATH)" "System.IterationPath=$(ADO_ITERATION_PATH)" \
        --query id -o tsv)

      az boards work-item relation add \
        --id "$feature_id" \
        --relation-type "System.LinkTypes.Hierarchy-Reverse" \
        --target-id "${{ parameters.epicId }}"
  env:
    AZURE_DEVOPS_EXT_PAT: $(ADO_PAT)
```

##### Automated State Updates from Pull Requests

```yaml
trigger: none
pr:
  branches:
    include:
    - main

pool:
  vmImage: ubuntu-latest

steps:
- task: AzureCLI@2
  displayName: Move linked work items to Code Review/Done
  inputs:
    scriptType: bash
    scriptLocation: inlineScript
    inlineScript: |
      az extension add --name azure-devops --only-show-errors
      az devops configure --defaults organization="$(ADO_ORG_URL)" project="$(ADO_PROJECT)"

      # Example: resolve linked work items from PR and update workflow state.
      # Replace with repository-specific logic (REST or CLI query).
      for id in $(echo "$(LINKED_WORK_ITEM_IDS)"); do
        az boards work-item update --id "$id" --fields "System.State=Code Review"
      done
```

### Work Item Creation Checklist

#### Pre-Creation Preparation

- [ ] **Feature artifacts complete**: PRD, UX design, technical breakdown, testing plan
- [ ] **Epic exists**: Parent epic work item created with proper fields and tags
- [ ] **Azure Board configured**: Columns, card rules, and team settings configured
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

This Azure DevOps project management approach ensures complete traceability from epic-level planning down to individual implementation tasks, with automated tracking and clear accountability for all team members.
