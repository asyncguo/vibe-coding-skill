# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Vibe Coding Skill** (vibe-coding-skill) is a community-driven repository for sharing and distributing reusable AI Agent skills for Claude Code, Codex, and similar AI programming assistants. The project provides plug-and-play commands (slash commands) that enhance AI-assisted development workflows.

**Primary Language**: Documentation (Markdown) - this is a skill/command distribution repository, not a code project.

**License**: MIT

## Repository Structure

```
claude-code/
└── commands/          # Claude Code slash commands (the core deliverable)
    ├── reflect.md     # Code reflection and critical analysis
    └── spec.md        # Requirements specification mode
```

Additional planned directories (not yet implemented):
- `skills/` - General-purpose skill library
- `examples/` - Usage examples and test scripts
- `docs/` - Development guides

## Core Skills

### 1. `/reflect` - Code Reflection and Critical Analysis
**Purpose**: Deep, objective, rigorous code analysis

**Key Features**:
- Adaptive analysis depth based on code type and scope
- Multi-dimensional evaluation (architecture, performance, security, maintainability)
- Structured output with severity levels (Critical/Significant/Improvement)
- Brutally honest assessment - no diplomatic hedging

**Code Type Categories Supported**:
- Business Logic Code
- API/Interface Code
- Infrastructure Code (IaC, Docker, K8s)
- Configuration Files
- Data Layer Code (schemas, migrations, queries)
- Frontend Code (components, state management)
- Test Code
- Build/Tooling Code (scripts, CI/CD)

**Scope-Based Analysis**:
- Small (<100 lines): 1-2 dimensions, actionable issues
- Medium (100-500 lines): 2-4 dimensions, pattern analysis
- Large (500+ lines): Architectural overview + critical path drill-down

### 2. `/spec` - Requirements Specification Mode
**Purpose**: Define WHAT to build from product/user perspective (not HOW)

**Key Features**:
- Three-tier detail levels (Simple/Standard/Complex features)
- MoSCoW prioritization (Must/Should/Could/Won't Have)
- Traceable requirements with unique IDs (REQ-###, BUS-###, Q-###, CONFLICT-###)
- Technology-agnostic specification (focus on behaviors, not implementations)
- Comprehensive framework covering functional, non-functional, business rules, acceptance criteria

**Complexity Guidelines**:
- Simple (<2 days): Sections 1, 2.2 (Must Have), 7, 9
- Standard (2-10 days): Sections 1, 2, 3, 7, 8, 9
- Complex (>10 days): All sections

## Contributing Skills

### File Naming Convention
- Use lowercase with hyphens: `my-skill.md`
- Keep names concise and descriptive
- Avoid special characters and spaces

### Required Skill Structure

1. **Front Matter** (YAML metadata):
```yaml
---
description: Brief skill description
argument-hint: <parameter hint>
---
```

2. **Core Sections**:
   - Functional description (what the skill does)
   - Usage guidelines (when and how to use)
   - Core principles (execution philosophy)
   - Framework/template (structured execution approach)
   - Examples (concrete usage demonstrations)

### Quality Standards
- Every skill must have clear, actionable purpose
- Include concrete usage examples
- Provide structured frameworks (not vague guidelines)
- Focus on specific, repeatable workflows
- Avoid generic advice that applies to all codebases

## Development Workflow

### Installation Testing
```bash
# Copy commands to Claude Code config directory
cp claude-code/commands/*.md ~/.claude/commands/

# Verify installation
# In Claude Code, type "/" to see available commands
```

### No Build/Test/Lint Commands
This repository contains only documentation/skill files. There are no build, test, or lint commands. Validation is manual:
1. Review markdown syntax
2. Test slash command execution in Claude Code
3. Verify command logic and output quality

## Branch Strategy
- `main` - Primary branch for all development and PRs

## Contribution Process

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-skill`
3. Add skill files to appropriate directory (`claude-code/commands/` for slash commands)
4. Follow skill structure and naming conventions
5. Test the skill in Claude Code
6. Commit: `git commit -m "feat: add skill for XXX"`
7. Push and create Pull Request with:
   - Detailed skill description
   - Use cases and scenarios
   - Usage examples/screenshots (if helpful)

## Key Principles for Skills

**For Reflection Skills**:
- Brutally honest, no diplomatic hedging
- Specific code locations (file:line references)
- Root cause analysis, not surface-level observations
- Measurable impact explanations
- Acknowledge quality when it exists (don't manufacture problems)

**For Specification Skills**:
- Define WHAT, not HOW
- User-centric focus (behaviors and outcomes)
- Testable and traceable requirements
- Technology-agnostic (unless mandated by business)
- Clear contract between stakeholders and engineers

## Community Resources

- **Discussions**: Use GitHub Discussions for general questions
- **Issues**: Report bugs or propose new skills via GitHub Issues
- **Roadmap**: See README.md for planned features (test generation, docs generation, bug analysis, etc.)
