# Build Anchor Document Prompts

## 1. Create Initial Anchor Structure

/\*\*

-   Create a new markdown anchor document at anchor/project-anchor.md with:
-
-   # Project Anchor Document
-
-   ## Table of Contents
-   -   Link to each section
-
-   ## Core Patterns
-   -   Base Entity type
-   -   Generic Repository interface
-   -   Generic Service interface
-   -   Common error types
-
-   ## [Domain] Domain (repeat for each domain)
-   -   Entity types
-   -   DTOs
-   -   Repository interface
-   -   Service interface
-   -   Business rules
-
-   ## API Contracts
-   -   Response format
-   -   Endpoint definitions
-
-   ## Database Schemas
-   -   Table structures
-
-   Use the types I've extracted from previous prompts
    \*/

## 2. Add Domain Section

/\*\*

-   Add a new section to anchor/project-anchor.md for [DOMAIN]:
-
-   ## [Domain] Domain
-
-   ### Types
-   ```typescript

    ```
-   // Main entity
-   export interface [Entity] extends Entity {
-   // properties from extraction
-   }
-
-   // DTOs
-   export interface Create[Entity]DTO {
-   // properties
-   }
-   ```

    ```
-
-   ### Repository
-   ```typescript

    ```
-   export interface [Entity]Repository extends Repository<[Entity]> {
-   // custom methods
-   }
-   ```

    ```
-
-   ### Business Rules
-   -   List validation rules
-   -   List constraints
-   -   List relationships
        \*/

## 3. Validate Completeness

/\*\*

-   Review anchor/project-anchor.md and check:
-
-   1. ✓ All domains have sections
-   2. ✓ All types are defined
-   3. ✓ No "any" types
-   4. ✓ All repos extend base Repository
-   5. ✓ All services extend base Service
-   6. ✓ Error types are comprehensive
-   7. ✓ API contracts match actual routes
-
-   List any missing items to add
    \*/
