# 📘 `Record<K, T>` — Utility Type in TypeScript

`Record<K, T>` is a built-in TypeScript utility type that allows you to define an object type with **specific keys** (`K`) and **value types** (`T`).

It's a concise and safe way to describe a key-value object shape.

---

## ✅ Syntax

```ts
Record<Keys, ValueType>
```

- `Keys`: the type of the object keys (e.g. string literals or `string`)
- `ValueType`: the type of the values for each key

---

## 🔧 Common Use Cases

- Mapping route names to components
- Creating enums or configuration objects
- Mapping language codes to translations
- Defining safe lookup tables

---

## Basic Example

```ts
type Role = "admin" | "user" | "guest";

const roleDescriptions: Record<Role, string> = {
  admin: "Has full access",
  user: "Can view and edit content",
  guest: "Read-only access",
};
```

💡 Here, TypeScript ensures:

- All keys (`admin`, `user`, `guest`) must be present
- All values must be `string`

---

## ⚛️ React Example: Mapping Slugs to Components

```tsx
import HomePage from "./pages/HomePage";
import AboutPage from "./pages/AboutPage";

type PageSlug = "home" | "about";

const pagesMap: Record<PageSlug, React.ReactNode> = {
  home: <HomePage />,
  about: <AboutPage />,
};
```

🔄 This pattern is useful for dynamic routing or rendering components from a slug (e.g. from `useParams()`).

---

## 🌐 Dynamic Key Example

If you don’t know the keys in advance:

```ts
const usersById: Record<string, User> = {};
```

This allows any string key, useful for ID-based lookups, e.g., `usersById["123"]`.

---

## 🚫 Gotchas

- If you use `Record<string, T>`, any string is allowed — not type-safe.
- Use **string literal unions** (e.g. `"home" | "about"`) to restrict allowed keys.

---

## 🧩 Related Utility Types

- `Partial<T>` – makes all properties optional
- `Pick<T, K>` – picks only a subset of properties
- `Omit<T, K>` – removes specific properties
- `Record<K, T>` – creates an object with specific keys and value types
