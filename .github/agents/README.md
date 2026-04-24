# 🤖 Custom Agents

Custom agents for GitHub Copilot, making it easy for users and organizations to "specialize" their Copilot coding agent (CCA) through simple file-based configuration.

### How to Use Custom Agents

**To Install:**
- Click the **VS Code** or **VS Code Insiders** install button for the agent you want to use
- Download the `*.agent.md` file and add it to your repository

**MCP Server Setup:**
- Each agent may require one or more MCP servers to function
- Click the MCP server to view it on the GitHub MCP registry
- Follow the guide on how to add the MCP server to your repository

**To Activate/Use:**
- Access installed agents through the VS Code Chat interface, assign them in CCA, or through Copilot CLI
- Agents will have access to tools from configured MCP servers
- Follow agent-specific instructions for optimal usage

| Title | Description | MCP Servers |
| ----- | ----------- | ----------- |
| [PostgreSQL Database Administrator](../agents/postgresql-dba.agent.md) | Work with PostgreSQL databases using the PostgreSQL extension. |  |
| [Create PRD Chat Mode](../agents/prd.agent.md) | Generate a comprehensive Product Requirements Document (PRD) in Markdown, detailing user stories, acceptance criteria, technical considerations, and metrics. |  |
| [Product Manager Jira Advisor](../agents/product-manager-advisor-jira.agent.md) | Product management guidance for creating Jira tickets, aligning business value with user needs, and making data-driven product decisions |  |
| [Software Engineer Agent](../agents/software-engineer.agent.md) | Expert-level software engineering agent. Deliver production-ready, maintainable code. Execute systematically and specification-driven. Document comprehensively. Operate autonomously and adaptively. |  |
| [Senior Cloud Architect](../agents/senior-cloud-architect.agent.md) | Expert in modern architecture design patterns, NFR requirements, and creating comprehensive architectural diagrams and documentation |  |
| [Azure SaaS Architect mode instructions](../agents/azure-saas-architect.agent.md) | Provide expert Azure SaaS Architect guidance focusing on multitenant applications using Azure Well-Architected SaaS principles and Microsoft best practices. |  |
| [Azure Principal Architect mode instructions](../agents/azure-principal-architect.agent.md) | Provide expert Azure Principal Architect guidance using Azure Well-Architected Framework principles and Microsoft best practices. |  |
| [API Architect](../agents/api-architect.agent.md) | Your role is that of an API architect. Help mentor the engineer by providing guidance, support, and working code. |  |
| [Project Architecture Planner](../agents/project-architecture-planner.agent.md) | Holistic software architecture planner that evaluates tech stacks, designs scalability roadmaps, performs cloud-agnostic cost analysis, reviews existing codebases, and delivers interactive Mermaid diagrams with HTML preview and draw.io export |  |
| [DevOps Expert](../agents/devops-expert.agent.md) | DevOps specialist following the infinity loop principle (Plan → Code → Build → Test → Release → Deploy → Operate → Monitor) with focus on automation, collaboration, and continuous improvement |  |
| [SE: DevOps/CI](../agents/se-gitops-ci-specialist.agent.md) | DevOps specialist for CI/CD pipelines, deployment debugging, and GitOps workflows focused on making deployments boring and reliable |  |

