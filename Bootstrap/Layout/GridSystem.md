# 🧩 Grid System

Bootstrap’s **Grid System** is a powerful layout mechanism based on **Flexbox**, designed for building responsive layouts by dividing the page into **rows** and **columns**.

---

## 📚 Table of Contents

1. [Flexbox Grid vs CSS Grid](#️-flexbox-grid-vs-css-grid)
2. [How it works](#-how-it-works)
3. [Equal vs Custom Column Widths](#-equal-vs-custom-column-widths)
4. [Responsive Columns](#-responsive-columns)
5. [Alignment](#alignment)
6. [Gutters (Spacing Between Columns)](#-gutters-spacing-between-columns)
7. [Utilities for Layout](#utilities-for-layout)
    - [Changing Display](#changing-display)
    - [Flexbox Options](#flexbox-options)
    - [Margin and Padding](#margin-and-padding)
    - [Toggle Visibility](#toggle-visibility)
8. [Z-index](#z-index)

---

## ⚙️ Flexbox Grid vs CSS Grid

| Feature         | Bootstrap Grid (Flexbox)                        | CSS Grid                                     |
| --------------- | ----------------------------------------------- | -------------------------------------------- |
| Direction       | One axis at a time                              | Both axes (2D)                               |
| Browser support | Excellent                                       | Very good                                    |
| Simplicity      | Easier for common layouts                       | More powerful/flexible                       |
| Use case        | Classic layouts (header/content/sidebar/footer) | Complex UIs with overlapping or nested zones |

> ✅ Bootstrap uses **Flexbox**, not native CSS Grid — easier to reason about with horizontal & vertical blocks.

---

## 🧱 How it works

Think of your layout as a **series of horizontal rows**, divided into **12 equal columns**. Each row must be wrapped in a `.row`, and columns are placed using `.col` classes.

```tsx
<div className="row">
  <div className="col-6">Left</div>
  <div className="col-6">Right</div>
</div>
```

> 💡 Like tables: each `.row` is a horizontal section, and `.col` are vertical slices inside it.

### Layout Example: Thinking in Grid

Imagine a basic page layout:

```text
[Navbar]         (horizontal section)
[Content]        (horizontal section)
 ├── Sidebar L   (vertical column)
 ├── Main Area   (vertical column)
 └── Sidebar R   (vertical column)
[Footer]         (horizontal section)
 ├── Logo        (vertical column)
 ├── Links       (vertical column)
 └── Projects    (vertical column)
```

In Bootstrap:

```tsx
<div className="container">
    <div className="row gx-2 py-2">
        <div className="col-3">Title</div>
        <div className="col-3">Searchbar</div>
        <div className="col-2">NavLink</div>
        <div className="col-2">NavLink</div>
        <div className="col-2">NavLink</div>
    </div>
    <div className="row gx-2 py-2">
        <div className="col-3">Sidebar L</div>
        <div className="col-6">Main</div>
        <div className="col-3">Sidebar R</div>
    </div>
    <div className="row gx-2 py-2">
        <div className="col-4">Logo</div>
        <div className="col-4">Links</div>
        <div className="col-4">Projects</div>
    </div>
</div>
```

---

## 📐 Equal vs Custom Column Widths

Bootstrap uses a **12-column grid**. You can:

### ✅ Equal columns (auto layout)

```tsx
<div className="row">
  <div className="col">One</div>
  <div className="col">Two</div>
</div>
```

Each `col` will split space equally (like `grid-cols-2` in Tailwind).

### 🛠️ Custom widths

```tsx
<div className="row">
  <div className="col-4">Sidebar</div>
  <div className="col-8">Main</div>
</div>
```

> 🔢 Add up to 12 per row. You can mix and match: `col-2`, `col-10`, etc.

---

## 📱 Responsive Columns

Use breakpoint prefixes (`sm`, `md`, `lg`, etc.) to change layout across screen sizes:

```tsx
<div className="row">
  <div className="col-12 col-md-4">Sidebar</div>
  <div className="col-12 col-md-8">Main</div>
</div>
```

> 📱 Stacked on mobile (`col-12`), horizontal on tablets and up (`col-md-*`)

---

## Alignment

### 🔼 Vertical alignment (within a `.row`)

Use `align-items-*` on `.row`:

- `align-items-start`
- `align-items-center`
- `align-items-end`

```tsx
<div className="row align-items-center">
  <div className="col">Top</div>
  <div className="col">Middle</div>
</div>
```

Or use `align-self-*` on individual `.col`:

```tsx
<div className="col align-self-end">This is aligned to bottom</div>
```

### ↔️ Horizontal alignment

Use `justify-content-*` on `.row`:

- `start`, `center`, `end`
- `between`, `around`, `evenly`

```tsx
<div className="row justify-content-between">
  <div className="col-3">Left</div>
  <div className="col-3">Right</div>
</div>
```

---

## 🧮 Gutters (Spacing Between Columns)

Bootstrap uses `g-`, `gx-`, and `gy-` for **gaps between columns** (like Tailwind’s `gap`, `gap-x`, `gap-y`):

```tsx
<div className="row gx-4 gy-2">
  <div className="col">Item 1</div>
  <div className="col">Item 2</div>
</div>
```

- `gx-*`: horizontal gap
- `gy-*`: vertical gap
- `g-*`: both

Values: `0` to `5`

---

## Utilities for Layout

Bootstrap provides a rich set of **utility classes** for faster mobile-friendly and responsive development. These classes help you with:

- Showing or hiding elements responsively
- Controlling display and flexbox behavior
- Applying margins and padding consistently
- Toggling visibility without affecting layout

### Changing Display

Use display utilities to responsively toggle common CSS `display` values.

```tsx
<div className="d-none d-md-block">Visible only on md and up</div>
<div className="d-flex justify-content-center">Flex container</div>
```

- `.d-flex` applies `display: flex`
- Responsive variants like `.d-sm-flex`, `.d-lg-none` apply display changes at breakpoints

> 💡 This is essential to combine with grid rows, columns, and other components to control visibility and layout precisely.

### Flexbox Options

While Bootstrap is built on flexbox, **not all elements are flex by default**. To enable flexbox utilities (alignment, sizing, spacing), add `.d-flex` or breakpoint variants.

```tsx
<div className="d-flex align-items-center">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

### Margin and Padding

Bootstrap includes a **six-level scale** for margin and padding utilities, based on the default spacer value (`1rem`).

```tsx
<div className="mb-3 p-2">Margin bottom 1rem, padding 0.5rem</div>
<div className="me-md-4">Margin end 1.5rem on md and up</div>
```

- `m` = margin, `p` = padding
- Direction: `t` (top), `b` (bottom), `s` (start), `e` (end), `x` (left+right), `y` (top+bottom)
- Responsive variants: `.me-md-3` applies at `md` breakpoint and up

### Toggle Visibility

Instead of toggling display, you can toggle **visibility**:

- `.visible` shows element (default)
- `.invisible` hides visually but **keeps element in layout**

```tsx
<div className="invisible">Hidden but still takes space</div>
```

---

## Z-index

Although **not part of the grid system**, `z-index` controls how components overlay and interact visually in Bootstrap.

### Bootstrap’s Z-index Scale

Bootstrap defines a set of standard `z-index` values to maintain layering consistency across components like:

- Dropdowns
- Sticky elements
- Modals
- Tooltips and popovers

| Component          | Z-index Value |
| ------------------ | ------------: |
| Dropdown           |          1000 |
| Sticky             |          1020 |
| Fixed              |          1030 |
| Offcanvas Backdrop |          1040 |
| Offcanvas          |          1045 |
| Modal Backdrop     |          1050 |
| Modal              |          1055 |
| Popover            |          1070 |
| Tooltip            |          1080 |
| Toast              |          1090 |

> ⚠️ These values are designed to avoid conflicts. Customizing individual z-index values is discouraged unless you update all consistently.
