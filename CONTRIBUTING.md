# TypeScript Coding Conventions

## Core Principles

1. **Strong Typing**: Use TypeScript's type system to its fullest extent
2. **Readability**: Write code that's easy to understand for other developers
3. **Maintainability**: Follow patterns that make future changes simpler
4. **Consistency**: Apply the same conventions throughout the codebase

## Variable Declarations

### Use `const` and `let` (Never `var`)

```typescript
// ✅ Good
const MAX_ITEMS = 100;   // For values that won't change
let counter = 0;         // For values that will change

// ❌ Bad
var userId = 42;         // 'var' has function scope, not block scope
```

### Always Add Type Annotations

```typescript
// ✅ Good
const username: string = 'alex';
const items: Array<Item> = [];
function calculateTotal(prices: number[]): number { /* ... */ }

// ❌ Bad
const username = 'alex';          // Relies on type inference
function process(data) { /* ... */ }  // Any type loses TypeScript benefits
```

### Use Explicit Return Types on Functions

```typescript
// ✅ Good
function getUserById(id: string): User | null { /* ... */ }
const formatPrice = (amount: number): string => `$${amount.toFixed(2)}`;

// ❌ Bad
function getUserById(id: string) { /* ... */ }  // Return type is implicit
```

## Function Design

### Prefer Arrow Functions

```typescript
// ✅ Good
const calculateTax = (amount: number, rate: number): number => {
  return amount * rate / 100;
};

// Also good for simple one-liners
const double = (x: number): number => x * 2;

// ❌ Not preferred (unless you need 'this' context)
function calculateTax(amount, rate) {
  return amount * rate / 100;
}
```

### Single Responsibility Principle

Each function should perform a single task:

```typescript
// ✅ Good: Single purpose function
const calculateTax = (amount: number, rate: number): number => {
  return amount * rate / 100;
};

// ❌ Bad: Function doing too much
const processOrder = (order: Order) => { 
  // hundreds of lines handling multiple concerns
};
```

### DRY (Don't Repeat Yourself)

Avoid code duplication by abstracting common operations:

```typescript
// ✅ Good: DRY
const applyDiscount = (product: Product, discountRate: number): void => {
  product.price = product.price * (1 - discountRate);
  product.lastUpdated = new Date();
};
products.forEach(p => applyDiscount(p, 0.1));
featuredProducts.forEach(p => applyDiscount(p, 0.15));

// ❌ Bad: Repetition
products.forEach(p => {
  p.price = p.price * 0.9;
  p.lastUpdated = new Date();
});
featuredProducts.forEach(p => {
  p.price = p.price * 0.85;
  p.lastUpdated = new Date();
});
```

## Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Variables | camelCase | `const userName = 'john';` |
| Functions | camelCase | `const calculateTotal = () => {};` |
| Classes | PascalCase | `class UserProfile {}` |
| Interfaces | PascalCase with descriptive name | `interface UserData {}` (not `IUserData`) |
| Types | PascalCase | `type UserType = {};` |
| Enums | PascalCase | `enum Direction { Up, Down }` |
| Constants | UPPER_SNAKE | `const MAX_RETRIES = 3;` |
| Private properties | camelCase with underscore prefix | `private _count: number;` |

### Descriptive Naming

```typescript
// ✅ Good
const getUsersByRole = (role: UserRole): User[] => { /* ... */ };
const isActive = user.status === 'active';

// ❌ Bad
const get = (r: UserRole): User[] => { /* ... */ };
const check = user.status === 'active';
```

## Code Structure

### Avoid Deep Nesting

Too many nesting levels make code harder to read:

```typescript
// ✅ Good: Early return pattern
if (!user) return null;
if (!user.isActive) return null;
if (!user.hasPermission) return null;

// Process valid user
doSomethingWithUser(user);

// ❌ Bad: Deep nesting
if (user) {
  if (user.isActive) {
    if (user.hasPermission) {
      // Process valid user
      doSomethingWithUser(user);
    }
  }
}
```

### Code Segmentation

Group related blocks of code with line breaks to improve readability:

```typescript
// User authentication logic
const validateCredentials = (email: string, password: string): boolean => {
  return isValidEmail(email) && passwordMeetsRequirements(password);
};

// User authorization logic
const hasAccess = (user: User, resource: Resource): boolean => {
  return user.permissions.includes(resource.requiredPermission);
};
```

### Indentation

Use proper indentation to mark the beginning and end of control structures:

```typescript
if (user.isAdmin) {
  console.log('Admin access granted');
  performAdminAction();
} else {
  console.log('Access denied');
}
```

## Formatting Guidelines

### Line Length

Keep lines reasonably short for better readability:

```typescript
// ✅ Good
const processComplexData = (data: ComplexType) => {
  return data.filter(item => 
    item.isValid && 
    item.type === 'important' && 
    !item.isArchived
  );
};

// ❌ Bad
const processComplexData = (data: ComplexType) => data.filter(item => item.isValid && item.type === 'important' && !item.isArchived);
```

## Import Organization

### Organize Imports by Source

```typescript
// External dependencies
import React, { useState, useEffect } from 'react';
import { connect } from 'react-redux';
import axios from 'axios';

// Internal modules
import { User } from '@/types';
import UserService from '@/services/UserService';
import { formatDate } from '@/utils/dateUtils';

// Local imports (same directory)
import './UserProfile.css';
import { ProfileHeader } from './ProfileHeader';
```

##
*These conventions aim to create consistent, maintainable code across our TypeScript projects. Suggestions for improvements are welcome through pull requests.*