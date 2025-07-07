# Project Anchor Document

> **SINGLE SOURCE OF TRUTH** - All types, interfaces, and patterns defined here
>
> ⚠️ **IMPORTANT**: This file is referenced by Copilot for ALL code generation
>
> 📅 **Last Updated**: [DATE]
>
> 🔒 **Status**: Add to .gitignore if contains sensitive business logic

## Table of Contents

1. [Core Patterns](#core-patterns)
2. [User Domain](#user-domain)
3. [Product Domain](#product-domain)
4. [API Contracts](#api-contracts)
5. [Database Schemas](#database-schemas)
6. [Error Handling](#error-handling)
7. [Configuration](#configuration)
8. [Testing Patterns](#testing-patterns)

---

## Core Patterns

### Base Entity

All entities in the system extend from this base:

**TypeScript:**

```typescript
export interface Entity {
    id: string;
    createdAt: Date;
    updatedAt: Date;
}
```

**Go:**

```go
type Entity struct {
    ID        string    `json:"id"`
    CreatedAt time.Time `json:"createdAt"`
    UpdatedAt time.Time `json:"updatedAt"`
}
```

### Repository Pattern

Generic repository interface for data access:

**TypeScript:**

```typescript
export interface Repository<T extends Entity> {
    findById(id: string): Promise<T | null>;
    findAll(filter?: Partial<T>): Promise<T[]>;
    save(entity: Omit<T, 'id' | 'createdAt' | 'updatedAt'>): Promise<T>;
    update(id: string, data: Partial<T>): Promise<T>;
    delete(id: string): Promise<boolean>;
}
```

### Service Pattern

Generic service interface for business logic:

**TypeScript:**

```typescript
export interface Service<T extends Entity> {
    get(id: string): Promise<T>;
    list(filter?: Partial<T>): Promise<T[]>;
    create(data: any): Promise<T>;
    update(id: string, data: any): Promise<T>;
    remove(id: string): Promise<void>;
}
```

---

## User Domain

### Types

```typescript
// Main entity
export interface User extends Entity {
    email: string;
    name: string;
    // TODO: Add your user fields
}

// DTOs
export interface CreateUserDTO {
    email: string;
    name: string;
    password: string;
}

export interface UpdateUserDTO {
    name?: string;
}

// Repository
export interface UserRepository extends Repository<User> {
    findByEmail(email: string): Promise<User | null>;
}

// Service
export interface UserService extends Service<User> {
    register(data: CreateUserDTO): Promise<User>;
    authenticate(email: string, password: string): Promise<{ user: User; token: string }>;
}
```

---

## Product Domain

### Types

```typescript
// TODO: Add your product domain types
export interface Product extends Entity {
    name: string;
    price: number;
}
```

---

## API Contracts

### Response Format

All API responses follow this format:

```typescript
export interface ApiResponse<T> {
    success: boolean;
    data?: T;
    error?: {
        code: string;
        message: string;
        details?: any;
    };
}
```

### Endpoints

```
Auth:
POST   /auth/login     - Login user
POST   /auth/register  - Register new user
POST   /auth/logout    - Logout user

Users:
GET    /users          - List users (admin only)
GET    /users/:id      - Get user by ID
PUT    /users/:id      - Update user
DELETE /users/:id      - Delete user

Products:
GET    /products       - List products
GET    /products/:id   - Get product
POST   /products       - Create product
PUT    /products/:id   - Update product
DELETE /products/:id   - Delete product
```

---

## Database Schemas

### Users Table

```sql
CREATE TABLE users (
  id VARCHAR(36) PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  name VARCHAR(255) NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

### Products Table

```sql
-- TODO: Add your product schema
```

---

## Error Handling

### Error Types

```typescript
export class AppError extends Error {
    constructor(message: string, public code: string, public statusCode: number) {
        super(message);
    }
}

export class NotFoundError extends AppError {
    constructor(resource: string, id: string) {
        super(`${resource} with id ${id} not found`, 'NOT_FOUND', 404);
    }
}

export class ValidationError extends AppError {
    constructor(message: string, public errors: Record<string, string>) {
        super(message, 'VALIDATION_ERROR', 400);
    }
}

export class UnauthorizedError extends AppError {
    constructor(message = 'Unauthorized') {
        super(message, 'UNAUTHORIZED', 401);
    }
}
```

---

## Configuration

### Environment Variables

```typescript
export interface Config {
    // Server
    PORT: number;
    NODE_ENV: 'development' | 'test' | 'production';

    // Database
    DB_HOST: string;
    DB_PORT: number;
    DB_NAME: string;
    DB_USER: string;
    DB_PASSWORD: string;

    // Auth
    JWT_SECRET: string;
    JWT_EXPIRES_IN: string;

    // TODO: Add your config
}
```

---

## Testing Patterns

### Unit Test Structure

```typescript
describe('ServiceName', () => {
    let service: ServiceName;
    let mockRepository: jest.Mocked<RepositoryName>;

    beforeEach(() => {
        mockRepository = createMockRepository();
        service = new ServiceName(mockRepository);
    });

    describe('methodName', () => {
        it('should handle happy path', async () => {
            // Arrange
            // Act
            // Assert
        });

        it('should handle error case', async () => {
            // Test error scenarios
        });
    });
});
```

---

## Usage Instructions

1. **For Copilot**: Reference this file in comments when generating code

    ```typescript
    // Implement UserService from anchor/project-anchor.md#user-domain
    ```

2. **For Developers**: Keep this document updated as the source of truth

3. **For New Features**: Add types here FIRST, then implement

---

## Notes

-   TODO: Fill in placeholders with your actual types
-   TODO: Add more domains as needed
-   TODO: Update database schemas
-   TODO: Add business rules section
