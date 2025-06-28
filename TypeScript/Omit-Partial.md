# TypeScript: Utility Types – `Omit`, `Partial` and `namespace`

- `Omit<T, K>` – remove properties from a type
- `Partial<T>` – make all properties optional
- `namespace` – group related code under a logical scope

---

## 📚 Table of Contents

- [`Omit<T, K>`](#-omitt-k)
- [`Partial<T>`](#-partialt)
- [Combining `Omit` & `Partial`](#-combining-omit-and-partial)
- [`namespace`](#-namespace)

---

## 🔹 `Omit<T, K>`

The `Omit` utility type allows you to construct a new type by **excluding one or more keys** from an existing type `T`.

- Syntax

```ts
Omit<Type, KeysToRemove>
```

- Example

```ts
type User = {
  id: number;
  name: string;
  email: string;
};

type UserWithoutEmail = Omit<User, 'email'>;

// Resulting type:
// {
//   id: number;
//   name: string;
// }
```

You can also omit multiple properties:

```ts
type NoIdOrEmail = Omit<User, 'id' | 'email'>;
```

- Use Case

When you want to reuse a type but exclude sensitive or internal fields, such as in API responses.

---

## 🔹 `Partial<T>`

The `Partial` utility type makes **all properties of a type optional**.

- Syntax

```ts
Partial<Type>
```

- Example

```ts
type User = {
  id: number;
  name: string;
  email: string;
};

type PartialUser = Partial<User>;

// Resulting type:
// {
//   id?: number;
//   name?: string;
//   email?: string;
// }
```

- Use Case

Useful when updating or patching a resource, like in a `PATCH` request:

```ts
function updateUser(id: number, data: Partial<User>) {
  // data can include any subset of User properties
}
```

---

## 🧪 Combining `Omit` and `Partial`

You can combine utility types to create more complex type transformations:

```ts
type User = {
  id: number;
  name: string;
  email: string;
};

// Create a type where `name` and `email` are optional, but `id` is still required
type EditableUser = {
  id: number;
} & Partial<Omit<User, 'id'>>;

// Equivalent to:
// {
//   id: number;
//   name?: string;
//   email?: string;
// }
```

---

## 🔹 `namespace`

Namespaces allow grouping code (types, functions, constants, etc.) under a single **logical scope** to avoid name collisions and improve organization.

- Syntax

```ts
namespace Name {
  export const value = ...;
  export function helper() { ... }
}
```

- Example

```ts
namespace Utils {
  export function greet(name: string) {
    return `Hello, ${name}!`;
  }

  export const PI = 3.14159;
}

console.log(Utils.greet('Alice')); // "Hello, Alice!"
```

- Use Case

While still valid, `namespace` is less common in modern TypeScript projects that use **ES modules** (`import`/`export`) for code organization.

> ❗ Best Practice: Prefer ES Modules unless you have a specific reason to use namespaces (e.g., in older codebases or when using global scripts).
