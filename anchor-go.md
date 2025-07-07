You're right - GitHub Copilot doesn't have a traditional system prompt, but here's how to make it understand your anchor system through strategic file placement and comment templates:

## Copilot Context Files

### 1. `.github/copilot-instructions.md`

Copilot reads this file for workspace context:

```markdown
# Copilot Instructions for This Project

## Architecture: Contract-Driven Development with Anchor Documents

This codebase follows a strict anchor document system:

-   `/anchors/modules/` - Contains behavioral contracts for each module
-   `/anchors/testing/` - Testing standards and patterns
-   `/patterns/` - Implementation patterns for all other concerns

## CRITICAL RULES:

1. **ALWAYS reference anchor documents** before generating code
2. **NEVER create new contracts** without updating anchors first
3. **Tests come FIRST** - follow TDD strictly
4. **Each module is independent** - no cross-module imports except through contracts

## Code Generation Process:

1. Check relevant module anchor for contracts
2. Check testing anchor for test patterns
3. Write tests following testing anchor
4. Implement to satisfy tests and contracts
5. Use patterns from /patterns/ for cross-cutting concerns

## Module Structure:
```

/[module]/
├── contracts.go # Interfaces from anchors/modules/[module].md
├── [module]\_test.go # Tests following anchors/testing/[module].md
└── impl.go # Implementation satisfying contracts

```

## Example References:
- "// Contract: anchors/modules/user.md#UserRepository"
- "// Pattern: patterns/error-handling.md#DomainErrors"
- "// Testing: anchors/testing/integration.md#DatabaseTests"
```

### 2. File Header Template

Put this at the top of each Go file:

```go
// Package [module] implements contracts defined in anchors/modules/[module].md
// Testing patterns: anchors/testing/[module].md
// Related patterns: patterns/[relevant-pattern].md
//
// Copilot: Generate code that strictly follows the contracts above.
// Do NOT introduce new public methods not defined in the anchor.
// All errors must follow patterns/error-handling.md

package [module]
```

### 3. Inline Prompt Templates

#### For New Features:

```go
// Feature: [FeatureName]
// Copilot Context:
// - Module contracts: anchors/modules/[module].md#[Contract]
// - Testing requirements: anchors/testing/[module].md#[TestType]
// - Error patterns: patterns/error-handling.md
// - Architecture: Each module is bounded context, communicate only through contracts
//
// Generate: [specific request]
```

#### For Test Generation:

```go
// Test Generation Context:
// - Contract under test: anchors/modules/[module].md#[Contract]
// - Testing pattern: anchors/testing/unit.md#[Pattern]
// - Test data builders: patterns/test-builders.md
//
// Generate Ginkgo tests that verify ALL contract behaviors including error cases
```

## Module-Based Anchor Example

Since you mentioned it feels like SPARC, here's a module anchor structure:

### `/anchors/modules/billing.md`

````markdown
# Billing Module Contracts

## Module Boundary

-   **Owns**: Subscriptions, Invoices, Payment Processing
-   **Depends On**: User (via UserID), Organization (via OrgID)
-   **Events Published**: BillingEvents (see Events section)

## Core Contracts

### BillingService

```go
type BillingService interface {
    // Subscription Management
    CreateSubscription(ctx context.Context, cmd CreateSubscriptionCommand) (*Subscription, error)

    // Payment Processing
    ProcessPayment(ctx context.Context, cmd ProcessPaymentCommand) (*Payment, error)

    // Query Operations
    GetInvoicesByCustomer(ctx context.Context, customerID string, filter InvoiceFilter) ([]*Invoice, error)
}
```
````

### BillingRepository

```go
type BillingRepository interface {
    // Transactional boundary - all or nothing
    CreateSubscriptionWithInitialInvoice(ctx context.Context, sub *Subscription, inv *Invoice) error

    // Queries respect module boundary
    FindActiveSubscriptionsByCustomer(ctx context.Context, customerID string) ([]*Subscription, error)
}
```

## Error Contracts

All errors in this module implement `BillingError`:

-   `ErrSubscriptionNotFound`
-   `ErrPaymentFailed`
-   `ErrInvoiceAlreadyPaid`

## Event Contracts

```go
type SubscriptionCreated struct {
    SubscriptionID string
    CustomerID     string
    PlanID        string
    CreatedAt     time.Time
}
```

````

### `/anchors/testing/billing.md`
```markdown
# Billing Module Testing Standards

## Test Organization
````

billing/
├── billing_test.go # Public API tests
├── internal_test.go # Internal implementation tests
└── integration_test.go # Database/external service tests

````

## Required Test Coverage

### 1. Contract Tests (MANDATORY)
Every public method in contracts MUST have:
- Happy path test
- Each error case test
- Boundary condition test

### 2. Integration Test Pattern
```go
var _ = Describe("BillingService Integration", func() {
    // Setup: Use test containers
    // Pattern: One test file per contract
    // Cleanup: Always rollback transactions
})
````

## Test Data Builders

Reference: patterns/test-builders.md#billing

````

## Practical Copilot Prompts for Your System

### 1. Starting a New Module
```go
// Copilot: Create skeleton for "notifications" module following our module structure:
// - Read anchors/modules/notifications.md for contracts
// - Create contracts.go with all interfaces
// - Create integration test file per anchors/testing/integration.md
// - Use patterns/module-structure.md for file organization
````

### 2. Adding Feature to Existing Module

```go
// Adding webhook support to billing module
// Copilot: Extend billing module with webhook notifications:
// 1. Current contracts: anchors/modules/billing.md
// 2. Webhook pattern: patterns/webhooks.md
// 3. Testing: anchors/testing/billing.md#WebhookTests
//
// Generate ONLY the test file first, following TDD
```

### 3. Cross-Module Integration

```go
// Copilot: Implement BillingUserAdapter that connects billing and user modules:
// - Billing contract: anchors/modules/billing.md#UserProvider
// - User contract: anchors/modules/user.md#UserQuery
// - Pattern: patterns/adapter.md
// - No direct module imports, only contract interfaces
```

This approach gives you:

-   Clear boundaries (SPARC-like)
-   Copilot always knows where to look
-   Consistent code generation
-   Module independence

Want me to create more specific examples for your particular module structure?
