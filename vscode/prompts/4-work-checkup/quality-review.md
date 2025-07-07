# Quality Review Prompts

## 1. Code Quality Checklist

/\*\*

-   Review this code for quality:
-
-   ## Clean Code
-   ✓ Functions < 20 lines
-   ✓ Descriptive names
-   ✓ No magic numbers
-   ✓ DRY principle
-   ✓ Single responsibility
-
-   ## Type Safety
-   ✓ No 'any' types
-   ✓ Proper null checks
-   ✓ Type guards where needed
-
-   ## Error Handling
-   ✓ All errors caught
-   ✓ Specific error types
-   ✓ Proper error messages
-
-   ## Testing
-   ✓ Unit tests exist
-   ✓ Edge cases covered
-   ✓ Mocks properly typed
-
-   Report issues with severity
    \*/

## 2. Performance Review

/\*\*

-   Review for performance issues:
-
-   Check for:
-   1. N+1 query problems
-   2. Missing database indexes
-   3. Inefficient loops
-   4. Memory leaks
-   5. Missing pagination
-   6. Synchronous operations
-
-   Suggest optimizations
    \*/

## 3. Security Review

/\*\*

-   Review for security issues:
-
-   Check for:
-   1. SQL injection risks
-   2. Missing input validation
-   3. Exposed sensitive data
-   4. Missing authentication
-   5. Improper error messages
-   6. Missing rate limiting
-
-   Flag critical issues
    \*/

## 4. Documentation Check

/\*\*

-   Check documentation completeness:
-
-   Verify:
-   1. ✓ All public methods have JSDoc
-   2. ✓ Complex logic is explained
-   3. ✓ README is updated
-   4. ✓ API docs match implementation
-   5. ✓ Examples provided
-
-   Generate missing documentation
    \*/
