# Tables

Bootstrap includes pre-styled, responsive, and customizable table components for displaying data in a structured way.

---

## 📚 Table of Contents

1. [Basic Table](#-basic-table)
2. [Table Variants](#-table-variants)
    - [Color Variants](#color-variants)
    - [Modifier Classes](#modifier-classes)
    - [Vertical Alignment](#vertical-alignment)
3. [Captions](#️-captions)
4. [Responsive Tables](#-responsive-tables)
5. [Aligning Content](#-aligning-content)
6. [Scope Attribute](#scope-attribute)
7. [Full Table Example](#full-table-example)

---

## 🔹 Basic Table

To get started, just use the `.table` className:

```tsx
<table className="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">First</th>
      <th scope="col">Last</th>
      <th scope="col">Handle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Mark</td>
      <td>Otto</td>
      <td>@motto</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Jacob</td>
      <td>Thornton</td>
      <td>@social</td>
    </tr>
  </tbody>
</table>
```

> ✅ Automatically adds spacing, borders, and light background for header rows.

---

## 🎨 Table Variants

You can customize tables using contextual classes and utility modifiers.

### Color Variants

```tsx
<table className="table table-success">...</table>
<tr className="table-warning">...</tr>
<td className="table-danger">...</td>
```

Available variants:

- `table-primary`
- `table-secondary`
- `table-success`
- `table-danger`
- `table-warning`
- `table-info`
- `table-light`
- `table-dark`

### Modifier Classes

- `.table-striped` → zebra-striped rows
- `.table-striped-columns` → zebra-striped **columns**
- `.table-hover` → highlights rows on hover
- `.table-bordered` → adds borders to all cells
- `.table-active` → highlights a specific row or cell
- `.table-sm` → compact version of the table
- `.table-group-divider` → adds a thick divider between `<thead>`, `<tbody>`, and `<tfoot>`

### Vertical Alignment

- Default:

  - `<thead>` cells → bottom
  - `<tbody>` cells → top
- You can override with:

  - `align-top`
  - `align-middle`
  - `align-bottom`

```tsx
<td className="align-middle">Centered vertically</td>
```

---

## 🏷️ Captions

Add a `<caption>` inside the `<table>` to describe its purpose:

```tsx
<table className="table">
  <caption>List of registered users</caption>
  {/* ... */}
</table>
```

> 📌 The caption is visually placed **above** the table by default. Add `.caption-top` to move it above.

```tsx
<table className="table caption-top">
  <caption>Employee data</caption>
</table>
```

---

## 📱 Responsive Tables

For horizontal scrolling on small screens, wrap the table in `.table-responsive`:

```tsx
<div className="table-responsive">
  <table className="table">
    {/- ... */}
  </table>
</div>
```

You can also limit responsiveness to specific breakpoints:

- `.table-responsive-sm`
- `.table-responsive-md`
- `.table-responsive-lg`
- `.table-responsive-xl`
- `.table-responsive-xxl`

---

## 🎯 Aligning Content

You can align text using:

- `text-start`, `text-center`, `text-end`
- `align-top`, `align-middle`, `align-bottom`

```tsx
<td className="text-center align-middle">Centered content</td>
```

---

## Scope Attribute

Use the `scope` attribute on `<th>` to improve accessibility:

- `scope="col"` → for column headers
- `scope="row"` → for row headers

```tsx
<th scope="row">1</th>
```

---

## Full Table Example

```tsx
<div className="table-responsive">
  <table className="table table-striped table-hover table-bordered table-sm align-middle">
    <thead className="table-dark text-center">
      <tr>
        <th scope="col">#</th>
        <th scope="col">User</th>
        <th scope="col">Email</th>
        <th scope="col">Status</th>
        <th scope="col">Role</th>
        <th scope="col">Last Login</th>
        <th scope="col">Actions</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th scope="row" className="text-center">1</th>
        <td>
          <div className="d-flex align-items-center gap-2">
            <img
              src="https://i.pravatar.cc/40?img=1"
              className="rounded-circle"
              width="40"
              height="40"
              alt="Avatar"
            />
            <div>
              <strong>John Doe</strong>
              <br />
              <small className="text-muted">CEO</small>
            </div>
          </div>
        </td>
        <td className="text-center">john@example.com</td>
        <td className="text-center">
          <span className="badge bg-success">Active</span>
        </td>
        <td className="text-center">Admin</td>
        <td className="text-center text-muted">2025-06-27</td>
        <td className="text-center">
          <button className="btn btn-sm btn-primary me-2">
            <i className="bi bi-pencil"></i>
          </button>
          <button className="btn btn-sm btn-danger">
            <i className="bi bi-trash"></i>
          </button>
        </td>
      </tr>

      <tr>
        <th scope="row" className="text-center">2</th>
        <td>
          <div className="d-flex align-items-center gap-2">
            <img
              src="https://i.pravatar.cc/40?img=5"
              className="rounded-circle"
              width="40"
              height="40"
              alt="Avatar"
            />
            <div>
              <strong>Jane Smith</strong>
              <br />
              <small className="text-muted">Product Manager</small>
            </div>
          </div>
        </td>
        <td className="text-center">jane@example.com</td>
        <td className="text-center">
          <span className="badge bg-warning text-dark">Pending</span>
        </td>
        <td className="text-center">Editor</td>
        <td className="text-center text-muted">2025-06-21</td>
        <td className="text-center">
          <button className="btn btn-sm btn-primary me-2">
            <i className="bi bi-pencil"></i>
          </button>
          <button className="btn btn-sm btn-danger">
            <i className="bi bi-trash"></i>
          </button>
        </td>
      </tr>

      <tr>
        <th scope="row" className="text-center">3</th>
        <td>
          <div className="d-flex align-items-center gap-2">
            <img
              src="https://i.pravatar.cc/40?img=8"
              className="rounded-circle"
              width="40"
              height="40"
              alt="Avatar"
            />
            <div>
              <strong>Alex Brown</strong>
              <br />
              <small className="text-muted">Intern</small>
            </div>
          </div>
        </td>
        <td className="text-center">alex@example.com</td>
        <td className="text-center">
          <span className="badge bg-secondary">Inactive</span>
        </td>
        <td className="text-center">Viewer</td>
        <td className="text-center text-muted">2025-05-30</td>
        <td className="text-center">
          <button className="btn btn-sm btn-primary me-2">
            <i className="bi bi-pencil"></i>
          </button>
          <button className="btn btn-sm btn-danger">
            <i className="bi bi-trash"></i>
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</div>
```
