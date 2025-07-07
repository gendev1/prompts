# Prompt to Generate Anchor Document

Copy and paste this into your editor with Copilot:

```
Analyze this codebase and create an anchor document (anchor/project-anchor.md) that serves as an AI context guide. DO NOT duplicate types that already exist in code - instead reference their locations.

The anchor document should include:

## 1. Project Overview
- Brief description of what this system does
- Key business domain (e.g., e-commerce, satellite tracking, etc.)
- Critical constraints or requirements

## 2. Architecture Patterns
- Overall architecture style (MVC, Clean, Hexagonal, etc.)
- How the code is organized (by feature, by layer, etc.)
- Key design patterns used consistently

## 3. Module/Domain Contexts
For each major module or domain in the codebase:
- Module name and purpose
- Location of types/models (e.g., "Types: `src/models/user.ts`")
- Business rules that aren't obvious from code
- Performance requirements
- Security considerations
- Common pitfalls or gotchas

## 4. Data Flow & Integration Points
- How services/modules communicate
- Event patterns (if any)
- API conventions
- Database conventions

## 5. Development Guidelines
- Coding patterns to follow
- Testing approach
- Error handling patterns
- Naming conventions

## 6. Performance Considerations
- Known bottlenecks
- Caching strategies
- Optimization guidelines
- Scaling considerations

## 7. Security & Compliance
- Authentication/authorization patterns
- Data privacy requirements
- Compliance needs (GDPR, HIPAA, etc.)
- Security conventions

## 8. Common Tasks & Patterns
- How to add a new feature
- How to modify existing functionality
- Debugging approaches
- Deployment considerations

## 9. Domain-Specific Context
- Business terminology
- Units and measurements (critical for scientific apps)
- Time zone handling
- Currency/money handling

## 10. What NOT to Do
- Anti-patterns to avoid
- Common mistakes
- Things that look helpful but break the system

Format this as a clean markdown document that provides CONTEXT for AI tools (Copilot, Claude, etc.) without duplicating actual code. Focus on the "why" and "how" rather than the "what" (which is in the code).

For each section, be specific to THIS codebase, not generic. Look for:
- Repeated patterns
- Comments that explain "why"
- Configuration files
- Test files (they often reveal intended behavior)
- README files
- Package.json or go.mod for dependencies

Remember: This document helps AI understand the PROJECT CONTEXT to generate better code. It's not documentation for humans - it's instructions for AI.
```

## 🎯 How to Use This Prompt

### Step 1: Position Your Cursor

```bash
# Create the file first
mkdir -p anchor
touch anchor/project-anchor.md
# Open it in VSCode
code anchor/project-anchor.md
```

### Step 2: Provide Context

Before the prompt, add a comment with basic info:

```markdown
<!--
Project: [Your Project Name]
Language: [TypeScript/Go/etc.]
Framework: [React/Express/etc.]
Team Size: [N developers]
Age: [6 months/2 years/etc.]
-->

[Paste the prompt above]
```

### Step 3: Let Copilot Work

-   Copilot will analyze your codebase
-   It will generate section by section
-   Accept suggestions that make sense
-   Skip or modify ones that don't

### Step 4: Refine with Specific Prompts

After the initial generation, add targeted prompts:

```markdown
<!-- Analyze the user management module and add specific context about our authentication flow, permission system, and the soft-delete requirement -->

<!-- Look at our screening service in Go and document the performance requirements, goroutine patterns, and why we use specific batch sizes -->

<!-- Find all the error handling patterns in the codebase and document when to use each type -->

<!-- Analyze our test files and document our testing philosophy and patterns -->
```

## 🔧 Refinement Checklist

After Copilot generates the initial anchor:

### ✅ Check for:

1. **Accuracy** - Is the context correct?
2. **Specificity** - Is it specific to YOUR project?
3. **No Type Duplication** - Are types referenced, not copied?
4. **Business Rules** - Are non-obvious rules captured?
5. **Performance Context** - Are critical performance needs noted?

### ❌ Remove:

1. **Generic advice** - "Use clean code principles"
2. **Duplicated types** - Full interface definitions
3. **Obvious stuff** - "Functions should have names"
4. **Implementation details** - That's what code is for

### ➕ Add:

1. **Specific measurements** - "Response time must be <100ms"
2. **Domain oddities** - "Satellite positions in meters, not km"
3. **Historical context** - "We tried X, it failed because Y"
4. **Integration secrets** - "The payment API has a 5 req/sec limit"

## 💡 Example Output Structure

Copilot should generate something like:

```markdown
# Project Anchor Document

## Project Overview

This is an e-commerce platform handling 50k orders/day with real-time inventory tracking...

## Architecture Patterns

-   Hexagonal architecture with ports and adapters
-   Domain models in `src/domain/`
-   Use cases in `src/application/`
-   Repository pattern for all data access

## Module: Order Management

Location: `src/modules/orders/`

Business Rules:

-   Orders cannot be modified after payment processing
-   Inventory must be reserved for 15 minutes during checkout
-   All prices in cents to avoid floating point issues

Performance:

-   Order creation must complete in <500ms
-   Bulk order export can be async (up to 5 min)

## Development Guidelines

When adding new features:

1. Start with use case in `application/`
2. Use existing repository patterns
3. Events published to 'order.\*' topics
4. All money amounts in cents
   ...
```

## 🚀 Pro Tips

1. **Run it multiple times** - Point it at different directories
2. **Use it for onboarding** - Great for new team members
3. **Keep it updated** - Add to it as you discover new patterns
4. **Version control it** - Track how your architecture evolves

This approach lets Copilot do the heavy lifting of analyzing your codebase, then you just refine and correct. Much faster than writing from scratch!

Want me to create more specific prompts for particular aspects of your codebase?
