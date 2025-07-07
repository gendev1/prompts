# Implementation Prompts

## 1. Implement from Test

/\*\*

-   Implement [CLASS_NAME] to pass all tests in [test-file].test.ts:
-
-   Requirements:
-   -   Must implement interface from anchor/project-anchor.md
-   -   All tests must pass
-   -   Use dependency injection pattern
-   -   No methods longer than 20 lines
-   -   Handle all error cases tested
-   -   Follow patterns from patterns/patterns-library.md
-
-   Do NOT:
-   -   Add methods not in tests
-   -   Use 'any' type
-   -   Access database directly in service layer
-   -   Throw generic errors
        \*/

## 2. Implement Repository

/\*\*

-   Implement [ENTITY]Repository:
-
-   Requirements:
-   -   Extends BaseRepository from patterns-library.md
-   -   Implements interface from anchor/project-anchor.md
-   -   All methods must handle database errors
-   -   Use parameterized queries
-   -   Support transactions
-   -   Log all queries in debug mode
-
-   Reference: patterns/repository-pattern.md
    \*/

## 3. Implement Service

/\*\*

-   Implement [ENTITY]Service:
-
-   Requirements:
-   -   Extends BaseService from patterns-library.md
-   -   Implements interface from anchor/project-anchor.md
-   -   Validate all inputs
-   -   Use repository for data access
-   -   Emit events for important operations
-   -   Handle business logic only
-
-   Reference: patterns/service-pattern.md
    \*/

## 4. Implement API Endpoint

/\*\*

-   Implement [ENDPOINT] controller:
-
-   Route: [METHOD] /api/[path]
-   Contract from anchor: [section reference]
-
-   Requirements:
-   -   Validate request body/params/query
-   -   Call appropriate service method
-   -   Return response matching anchor contract
-   -   Handle errors with proper status codes
-   -   Add request logging
-   -   Check authentication if needed
-
-   Reference: patterns/api-pattern.md
    \*/
