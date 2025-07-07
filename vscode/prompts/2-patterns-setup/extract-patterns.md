# Extract Patterns Prompts

## 1. Extract Repository Pattern

/\*\*

-   Looking at these repository implementations:
-
-   1. Find common methods across all repos
-   2. Identify the base pattern they follow
-   3. Extract transaction handling pattern
-   4. Extract error handling pattern
-   5. Extract query building pattern
-
-   Create a reusable BaseRepository class that:
-   -   Implements common methods
-   -   Can be extended by specific repos
-   -   Handles errors consistently
-   -   Supports transactions
        \*/

## 2. Extract Service Pattern

/\*\*

-   Looking at these service implementations:
-
-   1. Find common business logic patterns
-   2. Identify validation patterns
-   3. Extract authorization patterns
-   4. Extract event emission patterns
-   5. Extract logging patterns
-
-   Create a reusable BaseService class that:
-   -   Implements common operations
-   -   Provides hooks for validation
-   -   Handles errors consistently
-   -   Supports transactions
        \*/

## 3. Extract API Patterns

/\*\*

-   From these controllers/routes:
-
-   1. Extract request handling pattern
-   2. Extract validation pattern
-   3. Extract error response pattern
-   4. Extract pagination pattern
-   5. Extract authentication pattern
-
-   Create reusable:
-   -   BaseController class
-   -   Middleware functions
-   -   Response helpers
-   -   Validation helpers
        \*/
