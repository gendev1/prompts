# Extract Types Prompts

## 1. Extract Domain Types

/\*\*

-   From this [MODEL/ENTITY] file, extract and convert to clean types:
-
-   1. Remove all ORM decorators (@Entity, @Column, etc.)
-   2. Remove all method implementations
-   3. Keep only properties and their types
-   4. Create matching DTO interfaces:
-   -   Create[Entity]DTO (fields needed for creation)
-   -   Update[Entity]DTO (fields that can be updated)
-   -   [Entity]Response (fields returned to client)
-
-   Output as clean TypeScript interfaces or Go structs
    \*/

## 2. Extract Repository Interfaces

/\*\*

-   From this repository implementation, extract:
-
-   1. All method signatures (no implementation)
-   2. Return types and parameters
-   3. Custom query methods
-   4. Transaction methods if any
-
-   Create both:
-   -   Generic Repository<T> interface
-   -   Specific [Entity]Repository interface
        \*/

## 3. Extract Service Interfaces

/\*\*

-   From this service implementation, extract:
-
-   1. All public method signatures
-   2. Business logic method names and purposes
-   3. Dependencies injected in constructor
-   4. Return types including custom types
-
-   Create:
-   -   Generic Service<T> interface
-   -   Specific [Entity]Service interface
        \*/

## 4. Extract API Contracts

/\*\*

-   From these route/controller files, extract:
-
-   For each endpoint:
-   -   HTTP method and path
-   -   Request body type
-   -   Request params type
-   -   Request query type
-   -   Response success type
-   -   Response error types
-   -   Authentication requirements
-
-   Format as:
-   "[METHOD] /path": {
-   body?: Type,
-   params?: Type,
-   response: Type
-   }
    \*/
