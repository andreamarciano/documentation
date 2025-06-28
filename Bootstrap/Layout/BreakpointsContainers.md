# 🧱 Breakpoints and Containers

Bootstrap’s layout system is based on a **mobile-first** responsive approach, with fluid **containers** and customizable **breakpoints** that adapt to different screen sizes.

---

## 📚 Table of Contents

1. [Containers](#-containers)
2. [Breakpoints](#-breakpoints)
    - [Breakpoints & Container Widths](#-breakpoints--container-widths)
3. [Example: Responsive Padding](#example-responsive-padding)
4. [Example: Centered Layout with Breakpoint Container](#example-centered-layout-with-breakpoint-container)

---

## 📦 Containers

A **container** is the layout wrapper that centers your content and applies horizontal padding.

Bootstrap provides three main types of containers:

### 1. `.container`

A **responsive fixed-width container**, with max-width values that change at different breakpoints.

```tsx
<div className="container">
  <p>This content is centered and has padding.</p>
</div>
```

### 2. `.container-fluid`

A **full-width container**, spanning the entire width of the viewport.

```tsx
<div className="container-fluid">
  <p>This container stretches 100% of the viewport width.</p>
</div>
```

### 3. `.container-{breakpoint}`

A **responsive container** that behaves like `.container-fluid` until the specified breakpoint is reached, then becomes fixed-width.

```tsx
<div className="container-md">
  <p>This is full-width below `md`, and fixed-width `md` and up.</p>
</div>
```

> ✅ Useful when you want full-width behavior on mobile, but a centered layout on larger screens.

---

## 📐 Breakpoints

Bootstrap defines **5 main breakpoints** based on screen width:

| Breakpoint  | Abbreviation | Min Width | Example Use                |
| ----------- | ------------ | --------- | -------------------------- |
| Extra small | `xs`         | 0px       | Default (no suffix needed) |
| Small       | `sm`         | 576px     | Phones                     |
| Medium      | `md`         | 768px     | Tablets                    |
| Large       | `lg`         | 992px     | Laptops                    |
| Extra large | `xl`         | 1200px    | Desktops                   |
| XXL         | `xxl`        | 1400px    | Very large screens         |

> ⚠️ Bootstrap uses **mobile-first** classes, meaning styles apply from the given breakpoint and up.

---

### 📊 Breakpoints & Container Widths

This table shows how different `.container` classes behave across Bootstrap’s breakpoints:

| Class              | <576px(xs) | ≥576px(sm) | ≥768px(md) | ≥992px(lg) | ≥1200px(xl) | ≥1400px(xxl) |
| ------------------ | -------------- | -------------- | -------------- | -------------- | --------------- | ---------------- |
| `.container`       | 100%           | 540px          | 720px          | 960px          | 1140px          | 1320px           |
| `.container-sm`    | 100%           | 540px          | 720px          | 960px          | 1140px          | 1320px           |
| `.container-md`    | 100%           | 100%           | 720px          | 960px          | 1140px          | 1320px           |
| `.container-lg`    | 100%           | 100%           | 100%           | 960px          | 1140px          | 1320px           |
| `.container-xl`    | 100%           | 100%           | 100%           | 100%           | 1140px          | 1320px           |
| `.container-xxl`   | 100%           | 100%           | 100%           | 100%           | 100%            | 1320px           |
| `.container-fluid` | 100%           | 100%           | 100%           | 100%           | 100%            | 100%             |

> ℹ️ These values represent **maximum widths** applied at each breakpoint. Below the defined min-width, containers are 100% wide by default.

---

## Example: Responsive Padding

You can use responsive utility classes with breakpoints:

```tsx
<div className="p-2 p-md-4">
  <p>Padding is 0.5rem on mobile, and 1.5rem on md and up.</p>
</div>
```

---

## Example: Centered Layout with Breakpoint Container

```tsx
// App.tsx
return (
  <div className="container-lg mt-4">
    <h1 className="text-center">Responsive Layout</h1>
    <p>This layout is full-width on mobile, centered on large screens.</p>
  </div>
);
```

> 💡 Combine `.container-{breakpoint}` with utility classes like `mt-4`, `text-center`, and grid layout for flexible responsive pages.
