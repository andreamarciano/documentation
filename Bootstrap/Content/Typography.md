# ✍️ Typography

Bootstrap offers a rich set of typography utilities and components to style text elements consistently and responsively.

---

## 📚 Table of Contents

1. [Headings](#️-headings)
2. [Display Headings](#-display-headings)
3. [Lead Paragraph](#-lead-paragraph)
4. [Inline Text Elements](#️-inline-text-elements)
5. [Text and Color Utilities](#-text-and-color-utilities)
6. [Blockquotes](#-blockquotes)
7. [Lists](#-lists)
    - [Default Lists](#default-lists)
    - [Inline Lists](#inline-lists)
    - [Description Lists](#-description-lists)

---

## 🏷️ Headings

Bootstrap supports standard HTML headings (`<h1>` to `<h6>`) with default styles.

You can also apply heading styles to other elements by using `.h1`, `.h2`, etc. classes — useful if you want text with heading size but not semantic heading:

```tsx
// Semantic heading (recommended)
<h1>h1. Bootstrap heading</h1>

// Same style, non-heading element
<p className="h1">h1. Bootstrap heading</p>
```

---

## 🔠 Display Headings

Use `.display-1` to `.display-6` classes for larger, more prominent headings:

```tsx
<h1 className="display-1">Display 1</h1>
<h1 className="display-6">Display 6</h1>
```

---

## 📝 Lead Paragraph

The `.lead` class styles a paragraph to stand out as introductory text:

```tsx
<p className="lead">
  This is a lead paragraph. It stands out from regular paragraphs.
</p>
```

---

## ✂️ Inline Text Elements

Bootstrap respects standard inline HTML tags and styles them for clarity:

| Element    | Usage Example               | Description             |
| ---------- | --------------------------- | ----------------------- |
| `<mark>`   | `<mark>Highlighted</mark>`  | Highlight text          |
| `<del>`    | `<del>Deleted text</del>`   | Strikethrough           |
| `<s>`      | `<s>Strikethrough</s>`      | Alternate strikethrough |
| `<ins>`    | `<ins>Inserted text</ins>`  | Underlined text         |
| `<u>`      | `<u>Underlined</u>`         | Underlined text         |
| `<small>`  | `<small>Small text</small>` | Smaller text            |
| `<strong>` | `<strong>Bold</strong>`     | Bold text               |
| `<em>`     | `<em>Italic</em>`           | Italic text             |

---

## 🎨 Text and Color Utilities

Bootstrap includes many text utilities for alignment, transformation, and color:

```tsx
<p className="text-center text-primary text-uppercase">
  Centered, blue, uppercase text
</p>
```

Common classes:

- `text-start` | `text-center` | `text-end`
- `text-lowercase` | `text-uppercase` | `text-capitalize`
- Text color: `text-primary`, `text-success`, `text-danger`, etc.

---

## ❝ Blockquotes

Bootstrap styles blockquotes with padding, borders, and font styles:

```tsx
<blockquote className="blockquote">
  <p>This is a Bootstrap blockquote example.</p>
  <footer className="blockquote-footer">
    Someone famous in <cite title="Source Title">Source Title</cite>
  </footer>
</blockquote>
```

---

## 📋 Lists

### Default Lists

Bootstrap styles unordered and ordered lists normally:

```tsx
<ul>
  <li>First item</li>
  <li>Second item</li>
</ul>
```

### Inline Lists

Make lists inline, useful for navigation or tags:

```tsx
<ul className="list-inline">
  <li className="list-inline-item">Home</li>
  <li className="list-inline-item">About</li>
  <li className="list-inline-item">Contact</li>
</ul>
```

---

### 📄 Description Lists

Use description lists for key-value pairs or definitions:

```tsx
<dl>
  <dt>Term 1</dt>
  <dd>Description for term 1</dd>
  <dt>Term 2</dt>
  <dd>Description for term 2</dd>
</dl>
```
