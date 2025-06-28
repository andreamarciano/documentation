# 🧰 Helpers & Utilities

Bootstrap provides two categories of lightweight tools to control layout and appearance:

- Helpers → small, specific classes for accessibility, layout tricks, or visual tweaks.
- Utilities → general-purpose classes based on the --Utility API-- for fast styling without writing custom CSS.

> ⚠️ In practice, you'll use --Utilities-- almost all the time — Helpers are more niche but still useful.

---

## 📚 Table of Contents

1. [What’s the Difference?](#-whats-the-difference)
2. [Common Helpers](#-common-helpers)
3. [Overview of Utility Categories](#️-overview-of-utility-categories)
4. [Examples](#-examples)
5. [Bootstrap Utilities vs Tailwind](#bootstrap-utilities-vs-tailwind)

---

## ❓ What’s the Difference?

| Feature      | Helpers                        | Utilities                          |
| ------------ | ------------------------------ | ---------------------------------- |
| Purpose      | Specific helper functionality  | General-purpose styling            |
| Customizable | ❌ Not configurable             | ✅ Built on customizable API        |
| Frequency    | Used occasionally              | Used constantly                    |
| Examples     | `.clearfix`, `.stretched-link` | `.text-center`, `.mt-4`, `.d-flex` |

> 💡 Helpers are like “shortcuts” for one thing. Utilities are full tools.

---

## 🧷 Common Helpers

### 🔹 `.clearfix`

Force content to clear floated elements:

```tsx
<div className="clearfix"></div>
```

### 🔹 Color & background helpers

Apply contextual colors:

```tsx
<a href="#" className="link-danger">Delete</a>
```

### 🔹 `.stretched-link`

Make an entire container clickable when the link is inside:

```tsx
<div className="card">
  <div className="card-body">
    <h5 className="card-title">Card Title</h5>
    <a href="#" className="stretched-link">Read more</a>
  </div>
</div>
```

> 🧠 Requires `position: relative` on the parent (already set on `.card`)

### 🔹 `.text-truncate`

Truncate long text with ellipsis:

```tsx
<p className="text-truncate" style={{ maxWidth: "200px" }}>
  This is a long text that will be truncated.
</p>
```

### 🔹 `.visually-hidden`

Hide content visually but keep it for screen readers:

```tsx
<span className="visually-hidden">Screen-reader only text</span>
```

---

## ⚙️ Overview of Utility Categories

Bootstrap includes dozens of --utility classes--, which are highly reusable and responsive-ready:

### 📦 Layout & Positioning

- `.d-flex`, `.d-none`, `.position-relative`, `.top-0`, `.z-3`, `.ratio-16x9`

### 🖌️ Styling

- `.bg-primary`, `.text-success`, `.shadow`, `.border`, `.opacity-75`

### 📐 Sizing & Spacing

- `.w-100`, `.h-auto`, `.m-3`, `.p-4`, `.gap-2`

### 📲 Responsive Control

- `.d-sm-block`, `.text-md-start`, `.order-lg-2`

### Interaction & Visibility

- `.user-select-none`, `.overflow-auto`, `.visually-hidden`, `.pe-none`

### ⚙️ Utility API

Bootstrap's `scss/_utilities.scss` lets you generate custom utilities via configuration:

```scss
$utilities: (
  "spacing": (
    property: margin,
    class: m,
    values: (
      0: 0,
      1: 0.25rem,
      2: 0.5rem,
    )
  )
);
```

> 🧩 Advanced — for SCSS setups only.

---

## 🧪 Examples

### Stack items vertically

```tsx
<div className="vstack gap-3">
  <button className="btn btn-outline-primary">One</button>
  <button className="btn btn-outline-secondary">Two</button>
</div>
```

### Responsive image with fixed ratio

```tsx
<div className="ratio ratio-16x9">
  <iframe src="https://www.youtube.com/embed/example" allowFullScreen></iframe>
</div>
```

### Flexbox layout

```tsx
<div className="d-flex justify-content-between align-items-center">
  <span>Left</span>
  <span>Right</span>
</div>
```

### Truncated text with tooltip

```tsx
<p className="text-truncate" title="Full text here" style={{ maxWidth: "180px" }}>
  This is a long title that won’t fit in the box.
</p>
```

---

## Bootstrap Utilities vs Tailwind

Bootstrap and Tailwind share a common philosophy: **utility-first styling**.
This section compares Bootstrap's utilities with Tailwind CSS classes, to help understand how similar they really are.

> 💡 You can even **combine Bootstrap and Tailwind** in the same project (with care), but usually it’s best to pick one approach for consistency.

---

### Key Similarities

| Concept              | Bootstrap        | Tailwind       |
| -------------------- | ---------------- | -------------- |
| Margin top           | `.mt-3`          | `mt-3`         |
| Padding all sides    | `.p-4`           | `p-4`          |
| Flexbox container    | `.d-flex`        | `flex`         |
| Align center         | `.text-center`   | `text-center`  |
| Background color     | `.bg-primary`    | `bg-blue-500`  |
| Text color           | `.text-danger`   | `text-red-600` |
| Display none         | `.d-none`        | `hidden`       |
| Width 100%           | `.w-100`         | `w-full`       |
| Border radius        | `.rounded`       | `rounded`      |
| Shadow               | `.shadow`        | `shadow`       |
| Responsive left text | `.text-md-start` | `md:text-left` |

> ✅ If you're coming from Tailwind, Bootstrap’s utilities will feel very familiar.

---

### ⚠️ Key Differences

| Feature              | Bootstrap                        | Tailwind                           |
| -------------------- | -------------------------------- | ---------------------------------- |
| **Custom config?**   | Only with Sass/SCSS              | Fully customizable via config      |
| **Component-based?** | Yes (`.btn`, `.card`, etc.)      | No, everything is utility-based    |
| **Class names**      | Verbose (`.justify-content-end`) | Concise (`justify-end`)            |
| **Color system**     | Limited (primary, danger, etc.)  | Extensive scale (`gray-700`, etc.) |
| **Grid system**      | `.row`, `.col-*`, `.g-*`         | Custom flex/grid only              |

---

### Example

**Bootstrap:**

```tsx
<div className="d-flex justify-content-between align-items-center p-3 bg-light">
  <span>Hello</span>
  <span>World</span>
</div>
```

**Tailwind:**

```tsx
<div className="flex justify-between items-center p-3 bg-gray-100">
  <span>Hello</span>
  <span>World</span>
</div>
```
