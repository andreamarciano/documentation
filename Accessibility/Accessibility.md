# Accessibility with ARIA Attributes

## What is `aria-label`?

`aria-label` is an attribute used to define a string that labels an interactive element for assistive technologies (like screen readers). It helps users who cannot see the screen understand the purpose of elements that may not have visible text labels.

### Why use `aria-label`?

- To provide an accessible name for buttons, links, icons, and other UI elements.
- To clarify the purpose of elements that rely on icons or visuals only.
- To improve navigation and usability for screen reader users.

---

## 📚 Table of Contents

1. [Common ARIA Attributes Used](#common-aria-attributes-used)
    - [Detailed Descriptions](#detailed-descriptions)
2. [Additional Accessibility Attributes](#additional-accessibility-attributes)

---

## Common ARIA Attributes Used

| Attribute         | Purpose                                                                                        | Example Use Case                                             |
|-------------------|------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| `aria-label`      | Defines a string label for an element, overriding visible text if present.                     | Labeling a search button with an icon only.                  |
| `aria-haspopup`   | Indicates the element has a popup menu or dialog associated with it.                           | A dropdown toggle button.                                    |
| `aria-expanded`   | Indicates whether an expandable element (like dropdown) is open (`true`) or closed (`false`).  | A collapsible menu button.                                   |
| `aria-hidden`     | Marks an element as hidden from assistive technologies.                                        | Decorative icons that convey no additional info.             |
| `aria-labelledby` | References another element’s ID that serves as the accessible label.                           | A dropdown menu labelled by its toggle button.               |
| `aria-controls`   | References the ID of an element controlled or affected by the current element.                 | Button that toggles a menu or modal.                         |

---

### Detailed Descriptions

### `aria-label`

- Use when there is no visible text label but you want to provide one for screen readers.

Example:

```jsx
<button aria-label="Close menu">
  <i className="icon-close"></i>
</button>
```

### `aria-haspopup`

- Indicates presence of a popup menu or dialog.
- Values: `true` or more specific like `menu`, `dialog`.

Example:

```jsx
<button aria-haspopup="true" aria-expanded={isOpen}>Options</button>
```

### `aria-expanded`

- Used on expandable/collapsible controls.
- Boolean value (`true` or `false`) reflecting the state.

Example:

```jsx
<button aria-expanded={isOpen}>Toggle details</button>
```

### `aria-hidden`

- Hides elements from assistive technologies.
- Useful for purely decorative content.

Example:

```jsx
<i className="icon" aria-hidden="true"></i>
```

### `aria-labelledby`

- Points to another element’s ID for accessible name.
- Useful when label text is visually separate.

Example:

```jsx
<span id="menuLabel">Settings</span>
<ul aria-labelledby="menuLabel">...</ul>
```

### `aria-controls`

- Indicates which element(s) the current element controls.

Example:

```jsx
<button aria-controls="menu1" aria-expanded={isOpen}>Menu</button>
<ul id="menu1">...</ul>
```

---

## Additional Accessibility Attributes

| Attribute  | Purpose                                                                                    |
| ---------- | ------------------------------------------------------------------------------------------ |
| `role`     | Defines the semantic role of an element (e.g., `button`, `navigation`, `dialog`).          |
| `tabIndex` | Controls keyboard navigation order.                                                        |
| `alt`      | Provides text alternative for images (important for screen readers).                       |
| `title`    | Displays tooltip text on hover and can be read by some screen readers, but support varies. |
