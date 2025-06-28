# 🧩 Components

Bootstrap includes a wide range of **prebuilt components** to speed up UI development. Most components are accessible, responsive, and easily customizable using utility classes.

Below is a quick overview of the most common components with basic usage examples.

---

## 📚 Table of Contents

1. [Accordion](#-accordion)
2. [Alerts](#-alerts)
3. [Badge](#-badge)
4. [Breadcrumb](#-breadcrumb)
5. [Buttons](#-buttons)
    - [Button Group](#️-button-group)
    - [Close Button](#-close-button)
6. [Card](#-card)
7. [Carousel](#-carousel)
8. [Collapse](#-collapse)
9. [Dropdowns](#-dropdowns)
10. [List Group](#-list-group)
11. [Modal](#-modal)
12. [Navbar](#-navbar)
    - [Navs & Tabs](#-navs--tabs)
13. [Offcanvas](#-offcanvas)
14. [Pagination](#-pagination)
15. [Placeholders](#-placeholders)
16. [Popovers](#-popovers)
17. [Progress](#-progress)
18. [Scrollspy](#-scrollspy)
19. [Spinners](#-spinners)
20. [Toasts](#-toasts)
21. [Tooltips](#-tooltips)

---

## 🔽 Accordion

```tsx
<div className="accordion" id="accordionExample">
  <div className="accordion-item">
    <h2 className="accordion-header" id="headingOne">
      <button className="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne">
        Accordion Item #1
      </button>
    </h2>
    <div id="collapseOne" className="accordion-collapse collapse show">
      <div className="accordion-body">Hello accordion</div>
    </div>
  </div>
</div>
```

---

## 🚨 Alerts

```tsx
<div className="alert alert-warning" role="alert">
  This is a warning alert!
</div>
```

---

## 🔖 Badge

```tsx
<h4>Messages <span className="badge bg-primary">4</span></h4>
```

---

## 🧭 Breadcrumb

```tsx
<nav aria-label="breadcrumb">
  <ol className="breadcrumb">
    <li className="breadcrumb-item"><a href="#">Home</a></li>
    <li className="breadcrumb-item active" aria-current="page">Library</li>
  </ol>
</nav>
```

---

## 🔘 Buttons

```tsx
<button className="btn btn-primary">Click me</button>
```

### 🎛️ Button Group

```tsx
<div className="btn-group" role="group">
  <button className="btn btn-outline-primary">Left</button>
  <button className="btn btn-outline-primary">Right</button>
</div>
```

### ❌ Close Button

```tsx
<button type="button" className="btn-close" aria-label="Close"></button>
```

---

## 🧾 Card

```tsx
<div className="card" style={{ width: "18rem" }}>
  <div className="card-body">
    <h5 className="card-title">Card title</h5>
    <p className="card-text">Some quick content.</p>
    <a href="#" className="btn btn-primary">Go</a>
  </div>
</div>
```

---

## 🎠 Carousel

```tsx
<div id="carouselExample" className="carousel slide">
  <div className="carousel-inner">
    <div className="carousel-item active">
      <img src="..." className="d-block w-100" alt="..." />
    </div>
  </div>
</div>
```

---

## 📉 Collapse

```tsx
<button className="btn btn-primary" data-bs-toggle="collapse" data-bs-target="#collapseExample">
  Toggle
</button>
<div className="collapse mt-2" id="collapseExample">
  <div className="card card-body">Hidden content</div>
</div>
```

---

## 🧷 Dropdowns

```tsx
<div className="dropdown">
  <button className="btn btn-secondary dropdown-toggle" data-bs-toggle="dropdown">
    Menu
  </button>
  <ul className="dropdown-menu">
    <li><a className="dropdown-item" href="#">Action</a></li>
  </ul>
</div>
```

---

## 📋 List Group

```tsx
<ul className="list-group">
  <li className="list-group-item">Item 1</li>
  <li className="list-group-item">Item 2</li>
</ul>
```

---

## 🪟 Modal

```tsx
<button className="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
  Open Modal
</button>

<div className="modal fade" id="exampleModal">
  <div className="modal-dialog">
    <div className="modal-content">
      <div className="modal-header">
        <h5 className="modal-title">Modal Title</h5>
        <button className="btn-close" data-bs-dismiss="modal"></button>
      </div>
      <div className="modal-body">Modal content here.</div>
    </div>
  </div>
</div>
```

---

## 🧭 Navbar

```tsx
<nav className="navbar navbar-expand-lg navbar-light bg-light">
  <a className="navbar-brand" href="#">Brand</a>
</nav>
```

### 🧷 Navs & Tabs

```tsx
<ul className="nav nav-tabs">
  <li className="nav-item">
    <a className="nav-link active" href="#">Tab 1</a>
  </li>
</ul>
```

---

## 📥 Offcanvas

```tsx
<button className="btn btn-primary" data-bs-toggle="offcanvas" data-bs-target="#offcanvasExample">
  Open Menu
</button>

<div className="offcanvas offcanvas-start" id="offcanvasExample">
  <div className="offcanvas-header">
    <h5>Menu</h5>
    <button className="btn-close" data-bs-dismiss="offcanvas"></button>
  </div>
</div>
```

---

## 🔢 Pagination

```tsx
<nav>
  <ul className="pagination">
    <li className="page-item active"><a className="page-link" href="#">1</a></li>
    <li className="page-item"><a className="page-link" href="#">2</a></li>
  </ul>
</nav>
```

---

## ⏳ Placeholders

```tsx
<span className="placeholder col-6"></span>
```

---

## 💬 Popovers

```tsx
<button className="btn btn-secondary" data-bs-toggle="popover" title="Title" data-bs-content="Popover text">
  Toggle Popover
</button>
```

> ⚠️ Requires JS init: `bootstrap.Popover` on mount

---

## 📊 Progress

```tsx
<div className="progress">
  <div className="progress-bar" style={{ width: "60%" }}>60%</div>
</div>
```

---

## 📌 Scrollspy

```tsx
<body data-bs-spy="scroll" data-bs-target="#navbar-example" data-bs-offset="0">
  ...
</body>
```

> ⚠️ Needs `position-relative` and a scrollable container

---

## 🔄 Spinners

```tsx
<div className="spinner-border text-primary" role="status">
  <span className="visually-hidden">Loading...</span>
</div>
```

---

## 🍞 Toasts

```tsx
<div className="toast show">
  <div className="toast-header">
    <strong className="me-auto">Bootstrap</strong>
    <button className="btn-close" data-bs-dismiss="toast"></button>
  </div>
  <div className="toast-body">Hello, world!</div>
</div>
```

---

## 💡 Tooltips

```tsx
<button className="btn btn-secondary" data-bs-toggle="tooltip" title="Tooltip text">
  Hover me
</button>
```

> ⚠️ Requires JS init: `bootstrap.Tooltip` on mount
