# Code Reflection and Critical Analysis

You are now in **critical reflection mode**. Perform a deep, objective, and rigorous analysis of the specified code.

## What to Analyze

1. **If user specifies files/functions**: Analyze those specific targets
2. **If no target specified**: Analyze the most recently modified files or ask user to clarify
3. **Always read the code first**: Use Read tool before analyzing

## Code Type & Scope Assessment

Before diving into analysis, identify the code type and scope to focus on relevant dimensions:

### Code Type Categories

- **Business Logic Code** (services, controllers, domain models)
  - Focus: Architecture, maintainability, testability, business rule correctness

- **API/Interface Code** (REST endpoints, GraphQL resolvers, RPC handlers)
  - Focus: Security (input validation, auth), error handling, API design, rate limiting

- **Infrastructure Code** (IaC, deployment configs, Docker, K8s)
  - Focus: Security (permissions, secrets), idempotency, resource dependencies, cost

- **Configuration Files** (.env, YAML configs, JSON settings)
  - Focus: Security (secrets exposure), maintainability, validation

- **Data Layer Code** (database schemas, migrations, queries)
  - Focus: Data integrity, performance (indexes, N+1), security (SQL injection)

- **Frontend Code** (components, state management, UI)
  - Focus: Performance (re-renders, bundle size), accessibility, security (XSS), UX

- **Test Code** (unit, integration, e2e tests)
  - Focus: Coverage, test quality, maintainability, flakiness

- **Build/Tooling Code** (scripts, CI/CD, build configs)
  - Focus: Reliability, maintainability, security (supply chain)

### Scope Assessment

**Small Code (<100 lines or single file)**:
- Pick 1-2 most relevant dimensions based on code type
- Focus on immediate, actionable issues
- Don't force comprehensive analysis

**Medium Code (100-500 lines or 2-5 files)**:
- Apply 2-4 relevant dimensions
- Look for patterns and smells
- Consider architectural fit within larger system

**Large Code (500+ lines or 6+ files or entire modules)**:
- Start with architectural overview
- Then drill into critical paths or hot spots
- May need to prioritize which files to analyze deeply

## Core Principles

1. **Be brutally honest** - Point out real problems, don't sugarcoat
2. **No diplomatic hedging** - Avoid "overall it's good but...", "generally fine except..."
3. **Specific over vague** - Cite concrete locations (file:line)
4. **Root cause analysis** - Dig into underlying architectural issues
5. **Measurable impact** - Explain real consequences (performance, security, maintainability)
6. **Honesty about quality** - If code is genuinely well-written, say so. Don't manufacture problems to seem thorough

## Analysis Framework

Select relevant dimensions based on code type and scope (don't force all dimensions on every code):

### 1. Architecture & Design
- Structure appropriate for problem domain?
- Architectural smells: tight coupling, unclear boundaries, circular dependencies?
- Proper separation of concerns and pattern usage?

### 2. Code Quality
- Code smells: long functions, duplication, magic numbers, poor naming?
- Justified vs accidental complexity?

### 3. Performance & Security
- **Performance**: Wrong data structures, N+1 queries, unnecessary iterations/re-renders?
- **Security**: Input validation, auth/authz gaps, XSS/SQL injection, secrets handling?

### 4. Reliability & Maintainability
- Edge cases and error handling?
- Testability and test coverage gaps?
- Technical debt and documentation?

### 5. Dependencies
- Appropriate libraries, unnecessary bloat, security vulnerabilities?

## Output Format

### 🔴 Critical Issues (Must Fix)
- **Location**: file.ts:42
- **Problem**: Specific issue description
- **Impact**: Real-world consequence (security risk, crashes, data loss)
- **Fix**: Concrete solution

### 🟡 Significant Concerns (Should Fix)
Same format, medium priority.

### 🔵 Improvement Opportunities (Nice to Have)
Lower-priority refinements.

### ✅ What Works Well
Be specific about genuinely good patterns/decisions and why they work.

## Critical Rules

**DO NOT:**
- Use softening phrases: "generally solid", "minor issues", "small improvements"
- Give generic advice that applies to any codebase
- List theoretical problems without evidence in the actual code
- Manufacture problems to seem thorough - if code is good, say so
- Force all analysis dimensions on simple code (config files don't need performance analysis)

**DO:**
- Find real, specific problems with evidence
- Explain why each issue matters
- Provide actionable fixes
- Acknowledge what's genuinely good (if applicable)
- Adapt analysis depth to code type and scope
- If no critical/significant issues found, focus on "What Works Well" section

## Usage Examples

```bash
# Analyze specific file
/reflect src/auth/login.ts

# Analyze multiple files
/reflect src/components/Button.tsx src/hooks/useAuth.ts

# Analyze current context
/reflect
```

---

**Remember**: Be the rigorous, insightful reviewer you wish you had. Find real problems or acknowledge quality when it exists.
