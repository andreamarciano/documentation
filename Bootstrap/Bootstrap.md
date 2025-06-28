# Bootstrap

Bootstrap is one of the most popular front-end frameworks for building responsive and mobile-first websites. It offers a wide range of pre-styled components and utilities that help developers build consistent UIs faster and with less effort.

Key reasons to use Bootstrap:

- **Fast development:** Quickly build prototypes or production-ready UIs.
- **Consistency:** A unified design system maintained by the community.
- **Responsiveness:** Built-in grid system and responsive utilities.
- **Customizable:** Easily extend or override styles with Sass.

---

## 📚 Table of Contents

1. [How Bootstrap Works](#how-bootstrap-works)
2. [Bootstrap vs Tailwind](#bootstrap-vs-tailwind)
   - [Similar Utility Classes](#similar-utility-classes)
3. [Install Bootstrap](#install-bootstrap)
4. [Classic CSS vs Sass](#classic-css-vs-sass-which-one-should-you-import)
   - [Example: CSS vs SCSS](#example-css-vs-scss)

---

## How Bootstrap Works

Bootstrap provides a collection of CSS classes and JavaScript components that follow a design system. It includes:

- A 12-column responsive grid system
- Utility classes (spacing, colors, display, etc.)
- Pre-built components (buttons, modals, cards, alerts, etc.)
- JavaScript plugins powered by Popper.js

---

## Bootstrap vs Tailwind

| Feature             | Bootstrap                            | Tailwind CSS                         |
|---------------------|---------------------------------------|--------------------------------------|
| Approach            | Component-based                       | Utility-first                        |
| Learning Curve      | Easier for beginners                  | Steeper at first                     |
| Design System       | Built-in theme and components         | No predefined styles                 |
| Customization       | Customizable via Sass variables       | Highly customizable via config file |
| Size (default)      | Larger due to included styles         | Smaller (especially with PurgeCSS)   |
| Usage               | Add class names to HTML elements      | Compose custom UIs using utilities   |

Both are powerful, and the choice depends on your project needs and team preferences.

### Similar Utility Classes

| **Category**       | **Bootstrap (v5)**          | **Tailwind CSS**                | **Notes**                                                                  |
| ------------------ | --------------------------- | ------------------------------- | -------------------------------------------------------------------------- |
| **Margin**         | `mt-3`, `mb-2`, `mx-auto`   | `mt-3`, `mb-2`, `mx-auto`       | Both use similar abbreviations (`m` = margin, `t` = top, `x` = left+right) |
| **Padding**        | `pt-4`, `py-1`              | `pt-4`, `py-1`                  | Same structure (`p` = padding, `y` = top+bottom)                           |
| **Text Align**     | `text-center`               | `text-center`                   | Class name is identical                                                    |
| **Display**        | `d-flex`, `d-none`          | `flex`, `hidden`                | Different naming, same behavior                                            |
| **Flex Utilities** | `justify-content-center`    | `justify-center`                | Similar purpose, different syntax                                          |
| **Text Color**     | `text-danger`, `text-muted` | `text-red-500`, `text-gray-500` | Same purpose, but Bootstrap uses semantic names                            |
| **Backgrounds**    | `bg-primary`, `bg-dark`     | `bg-blue-500`, `bg-gray-900`    | Bootstrap uses semantic colors, Tailwind uses numeric scales               |

---

## Install Bootstrap

To use Bootstrap in a modern frontend stack (like Vite + React), we follow these steps:

### 1. Install Bootstrap and Popper.js

Bootstrap components like dropdowns, tooltips, and popovers require **`Popper.js`** for dynamic positioning. If you're planning to use those features, install it together with Bootstrap:

```bash
npm install bootstrap @popperjs/core bootstrap-icons
```

### 2. Install Sass (optional but recommended)

Bootstrap is built with `Sass`, a CSS preprocessor that allows you to customize Bootstrap’s variables, themes, and components.

To enable `Sass` customization (e.g., changing colors, spacing, breakpoints), install it:

```bash
npm install --save-dev sass
```

### 3. Import Bootstrap styles

In your main file, import the styles:

```tsx
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap-icons/font/bootstrap-icons.css";
```

---

## Classic CSS vs Sass: which one should you import?

There are two ways to import Bootstrap styles into your project, depending on your needs:

### Option 1: Precompiled CSS (easier)

```ts
import "bootstrap/dist/css/bootstrap.min.css";
```

- ✅ Quick and easy to set up
- ❌ You **cannot customize** Bootstrap’s variables (like colors or spacing)
- ⚠️ Don't import the SCSS file if you use this

### Option 2: SCSS source file (recommended for customization)

```ts
import "bootstrap/scss/bootstrap.scss";
```

- ✅ Enables full **Sass customization**
- ✅ Lets you override Bootstrap variables and selectively import modules
- 🛠️ Requires `sass` installed
- ⚠️ **Do not combine** with the precompiled CSS import (it causes conflicts)

### Which one should I use?

- Stick with **Option 1 (precompiled CSS)** if you're just learning or building small prototypes.
- Use **Option 2 (SCSS)** if you want to:

  - Customize Bootstrap's design system
  - Remove unused components
  - Optimize performance in production

---

### Example: CSS vs SCSS

#### 🔵 Using precompiled CSS (default look)

```tsx
// src/main.tsx
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap-icons/font/bootstrap-icons.css";

<h1 className="text-center p-4 text-primary">Welcome</h1>
<i className="bi bi-house"></i>
```

> ✅ This will show the default Bootstrap **blue** primary color.

#### 🟢 Using SCSS with a custom primary color

```tsx
// src/main.tsx
import "./styles/custom-bootstrap.scss";
import "bootstrap-icons/font/bootstrap-icons.css";
```

```scss
// src/styles/custom-bootstrap.scss

// Override default Bootstrap variables
$primary: #e91e63; // Custom pink
$font-family-base: 'Segoe UI', sans-serif;

// Import Bootstrap’s full SCSS
@import "bootstrap/scss/bootstrap";
```

```tsx
<h1 className="text-center p-4 text-primary">Welcome</h1>
<i className="bi bi-house"></i>
```

> 🎨 This will show the **custom pink** color instead of Bootstrap’s default blue.
