# Breadcrumb Navigation

**Breadcrumb navigation** is a secondary navigation system that shows a user's location within a website or application hierarchy. It's typically displayed as a horizontal list of links, like:

```text
Home / Settings / Users
```

---

## 📚 Table of Contents

1. [When Should You Use Breadcrumbs](#when-should-you-use-breadcrumbs)
2. [Types of Breadcrumbs](#types-of-breadcrumbs)
3. [Simple Example (HTML + CSS)](#simple-example-html--css)
4. [Example in React](#example-in-react)

---

## When Should You Use Breadcrumbs?

Breadcrumbs are most useful when:

- Your app/website has **nested content** or **hierarchical structure**
- Users often **navigate deep** into sections or categories
- You want to **improve navigation and orientation**

They're less useful in flat or single-level navigation systems (like landing pages or dashboards with no nesting).

---

## Types of Breadcrumbs

There are three main types:

### 1. **Location-Based**

Shows the actual location within the hierarchy.

```text
Dashboard / Users / John Doe / Settings
```

### 2. **Path-Based**

Shows the path the user took to reach the current page.

```text
Home / Search / Results / Selected Item
```

### 3. **Attribute-Based**

Used mainly in e-commerce to show filters or product categories.

```text
Home / Clothing / Men / Jackets / Size: M
```

---

## Simple Example (HTML + CSS)

```html
<nav class="breadcrumb">
  <a href="/">Home</a> /
  <a href="/settings">Settings</a> /
  <span>Users</span>
</nav>
```

```css
.breadcrumb {
  font-size: 0.95rem;
  margin: 1rem 0;
  color: #555;
}
.breadcrumb a {
  text-decoration: none;
  color: #007bff;
}
.breadcrumb span {
  font-weight: bold;
  color: #333;
}
```

---

## Example in React

```tsx
import { Link, useLocation } from "react-router-dom";

const Breadcrumbs = () => {
  const location = useLocation();
  const pathnames = location.pathname.split("/").filter(Boolean);

  return (
    <nav className="breadcrumb">
      <Link to="/">Home</Link>
      {pathnames.map((value, index) => {
        const to = "/" + pathnames.slice(0, index + 1).join("/");
        const isLast = index === pathnames.length - 1;

        return isLast ? (
          <span key={to}> / {decodeURIComponent(value)}</span>
        ) : (
          <span key={to}>
            {" "}
            / <Link to={to}>{decodeURIComponent(value)}</Link>
          </span>
        );
      })}
    </nav>
  );
};
```
