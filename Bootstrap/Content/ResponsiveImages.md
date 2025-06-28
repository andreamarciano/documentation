# 🖼️ Images

Bootstrap provides several utilities and components to work with images responsively and with proper styling.

---

## 📚 Table of Contents

1. [Responsive Images: `.img-fluid`](#-responsive-images-img-fluid)
2. [Thumbnails: `.img-thumbnail`](#️-thumbnails-img-thumbnail)
3. [Aligning Images](#️-aligning-images)
4. [Responsive Picture Element](#-responsive-picture-element)
5. [Figures with Captions](#️-figures-with-captions)

---

## 💧 Responsive Images: `.img-fluid`

Make images scale nicely to the parent container by adding `.img-fluid` class:

```tsx
<img src="path/to/image.jpg" alt="Example" className="img-fluid" />
```

> ✅ Adds `max-width: 100%` and `height: auto` to keep aspect ratio and responsiveness.

---

## 🖼️ Thumbnails: `.img-thumbnail`

To add a border and padding to images, use `.img-thumbnail`:

```tsx
<img src="path/to/image.jpg" alt="Thumbnail" className="img-thumbnail" />
```

> Adds rounded corners, border, and some padding.

---

## ↔️ Aligning Images

Bootstrap uses standard utilities for alignment inside containers or with text:

* **Float utilities:** `.float-start`, `.float-end`, `.float-none`

```tsx
<img src="image.jpg" className="img-fluid float-start" alt="Float left" />
```

* **Text alignment:** wrap image in a container with `text-center`, `text-end`, etc.

```tsx
<div className="text-center">
  <img src="image.jpg" className="img-fluid" alt="Centered" />
</div>
```

---

## 🌄 Responsive Picture Element

Use `<picture>` to serve different image sources for various formats or sizes:

```tsx
<picture>
  <source srcSet="image.webp" type="image/webp" />
  <source srcSet="image.jpg" type="image/jpeg" />
  <img src="image.jpg" alt="Example" className="img-fluid" />
</picture>
```

> ⚠️ **Apply classes like `.img-fluid` to the `<img>` tag, not `<picture>`.**

---

## 🖼️ Figures with Captions

Use the `.figure` component for images with optional captions:

```tsx
<figure className="figure">
  <img src="image.jpg" className="figure-img img-fluid rounded" alt="A rounded image" />
  <figcaption className="figure-caption text-center">
    A caption for the above image.
  </figcaption>
</figure>
```

> `.figure-img` styles the image; `.figure-caption` styles the caption.
