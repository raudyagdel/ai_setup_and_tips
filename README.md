# AI Setup & Tips

> A comprehensive collection of AI assistant configuration files and instructions for software development projects. Configure GitHub Copilot, Claude, OpenAI Codex, and Google Gemini with consistent, enterprise-grade coding standards.

## 📋 Overview

This repository contains templates and configuration files to standardize AI-assisted development across different platforms. Whether you're working on backend services with Spring Boot or frontend applications with Angular, these configurations ensure consistent code generation and best practices.

## 📁 Repository Structure

```
.
├── .agents/                       # All agent skills and definitions
│   ├── skills/                    # Specialized skills for different domains
│   └── ...                        # Additional agent resources
├── .github/
│   └── copilot-instructions.md    # GitHub Copilot configuration
├── AGENTS_BACKEND_TEMPLATE.md     # Backend AI agents (Spring Boot)
├── AGENTS_FRONT_TEMPLATE.md       # Frontend AI agents (Angular/Tailwind)
├── AGENTS_SKILLS.md               # Complete agent roles with assigned skills
├── GEMINI.md                      # Google Gemini instructions
├── codex.md                       # OpenAI Codex instructions
├── claude.md                      # Anthropic Claude instructions
├── mcp.json                       # Model Context Protocol configuration
├── PROMPT_TIPS.md                 # Prompt engineering tips
└── xml/
    └── funct_prog_prompt.xml      # Functional programming prompts
```

## 🚀 Quick Start

### 1. Agent Skills Management

The `.agents` folder contains all available agent skills for both backend and frontend development. These skills are organized by domain and purpose:

- **AGENTS_SKILLS.md** - Complete reference documenting all agent roles with their assigned skills
- `.agents/skills/` - Individual skill implementations

To understand which agents have which skills, refer to [AGENTS_SKILLS.md](./AGENTS_SKILLS.md).

> **Note:** To create new agents or update existing ones, use the `agent_generator` or `agent_updater` tools. These tools ensure consistency and proper skill assignment across your agent ecosystem.

### 2. GitHub Copilot Setup

Copy the `.github/copilot-instructions.md` file to your project's `.github` folder:

```bash
mkdir -p your-project/.github
cp .github/copilot-instructions.md your-project/.github/
```

### 3. MCP (Model Context Protocol) Configuration

The `mcp.json` file contains MCP server configurations for enhanced AI capabilities:

```json
{
    "mcpServers": {
        "angular-cli": {
            "command": "npx",
            "args": ["-y", "@angular/cli", "mcp"]
        },
        "context7": {
            "command": "npx",
            "args": ["-y", "@upstash/context7-mcp"],
            "env": {
                "CONTEXT7_API_KEY": "YOUR_API_KEY"
            }
        }
    }
}
```

**Usage:** Copy this file to your VS Code settings or project root and update API keys.

### 4. Backend AI Agents (Spring Boot)

The `AGENTS_BACKEND_TEMPLATE.md` defines specialized agents for Java/Spring Boot development:

| Agent | Role | Use Case |
|-------|------|----------|
| **ArchitectAgent** | System Architecture & Design | Microservices design, API design, database schema |
| **CodeGenAgent** | Code Generator | Entities, DTOs, services, controllers |
| **TestingAgent** | Test Generation | JUnit 5, Mockito, TestContainers |
| **SecurityAgent** | Security Audit | OWASP Top 10, authentication, authorization |
| **PerformanceAgent** | Performance Optimization | Query optimization, caching, JVM tuning |
| **DatabaseAgent** | Database Design | Schema design, migrations, indexing |
| **DevOpsAgent** | Deployment & Infrastructure | Docker, Kubernetes, CI/CD |
| **DocumentationAgent** | Documentation | OpenAPI specs, README, guides |
| **ReviewAgent** | Code Review | SOLID principles, best practices |
| **DebuggingAgent** | Problem Diagnosis | Error analysis, root cause investigation |

### 5. Frontend AI Agents (Angular)

The `AGENTS_FRONT_TEMPLATE.md` defines specialized agents for Angular/Tailwind development:

| Agent | Role | Use Case |
|-------|------|----------|
| **FrontendArchitectAgent** | Frontend Architecture | Feature-based architecture, lazy loading |
| **AngularAgent** | Angular Specialist | Components, signals, routing |
| **TailwindAgent** | Styling Specialist | Utility-first CSS, theming |
| **UXAgent** | UI/UX & Accessibility | WCAG compliance, keyboard navigation |
| **StateAgent** | State Management | Signals, RxJS, NgRx |
| **FrontendSecurityAgent** | Frontend Security | XSS prevention, auth handling |
| **FrontendPerformanceAgent** | Performance | Bundle optimization, lazy loading |
| **FrontendTestingAgent** | Testing | Jest, Playwright, Cypress |

## 🤖 AI Platform Instructions

### Claude (Anthropic)

See [claude.md](./claude.md) for instructions on configuring Claude for your projects.

### Codex (OpenAI)

See [codex.md](./codex.md) for OpenAI Codex configuration guidelines.

### Gemini (Google)

See [GEMINI.md](./GEMINI.md) for Google Gemini setup instructions.

## 📝 How to Use These Files

### For New Projects

1. **Copy the relevant files** to your project repository
2. **Customize** the instructions based on your tech stack
3. **Update** API keys and environment-specific values
4. **Commit** the configuration files to your repo

### For Team Standardization

1. **Fork this repository** for your organization
2. **Adapt** the templates to your coding standards
3. **Distribute** to all development teams
4. **Review and update** periodically

## 🔧 Configuration Tips

### Copilot Instructions

- Place in `.github/copilot-instructions.md` at project root
- Instructions are automatically picked up by GitHub Copilot
- Customize for your specific framework versions and patterns

### MCP Servers

- Configure in VS Code settings or project `mcp.json`
- Add your API keys securely (use environment variables)
- Enable only the servers you need

### Agent Templates

- Use as reference when prompting AI assistants
- Copy specific agent definitions into your prompts
- Combine multiple agents for complex tasks

## 📚 Additional Resources

- [PROMPT_TIPS.md](./PROMPT_TIPS.md) - Best practices for AI prompting
- [xml/funct_prog_prompt.xml](./xml/funct_prog_prompt.xml) - Functional programming patterns

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests with:
- New agent definitions
- Updated best practices
- Additional AI platform configurations
- Bug fixes and improvements

## 📄 License

This project is open source. See [LICENSE](./LICENSE) for details.

---

**Note:** Remember to never commit sensitive information like API keys. Use environment variables or secure secret management.
