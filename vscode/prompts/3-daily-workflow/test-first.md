# Test-First Development Prompts

## 1. Generate Unit Test Suite

/\*\*

-   Generate comprehensive unit tests for [CLASS_NAME]:
-
-   Requirements:
-   -   Import types from anchor/project-anchor.md
-   -   Mock all dependencies using jest.fn() or similar
-   -   Group tests by method using describe blocks
-   -   Test these scenarios for each method:
-   ✓ Happy path
-   ✓ Null/undefined inputs
-   ✓ Empty arrays/objects
-   ✓ Invalid data
-   ✓ Error cases
-   ✓ Edge cases
-   -   Use AAA pattern (Arrange, Act, Assert)
-   -   Each test should have one clear assertion
-
-   Reference the interface from anchor document
    \*/

## 2. Generate Integration Test

/\*\*

-   Generate integration test for [FEATURE]:
-
-   Test the complete flow:
-   1. [Step 1 - e.g., Create user]
-   2. [Step 2 - e.g., Login]
-   3. [Step 3 - e.g., Access protected resource]
-
-   Requirements:
-   -   Use test database or in-memory DB
-   -   Clean up data after each test
-   -   Test actual integration points
-   -   Verify data persists correctly
-   -   Test error scenarios
-
-   Use types from anchor/project-anchor.md
    \*/

## 3. Generate E2E Test

/\*\*

-   Generate end-to-end test for [USER_FLOW]:
-
-   Test from API layer:
-   1. [API call 1]
-   2. [API call 2]
-   3. [Verify final state]
-
-   Requirements:
-   -   Use supertest or similar
-   -   Include auth if needed
-   -   Verify HTTP status codes
-   -   Verify response shapes match anchor types
-   -   Test error responses
        \*/

## 4. Quick Test Stub

// Generate failing test for [method_name] with TODO implementation
// Include all edge cases as separate it() blocks
// Reference types from anchor/project-anchor.md
