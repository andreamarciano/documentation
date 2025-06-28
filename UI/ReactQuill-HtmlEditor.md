# 📝 React Quill – Rich Text HTML Editor for React

**React Quill** is a powerful, customizable **WYSIWYG** (What You See Is What You Get) rich text editor built for React. It is a React wrapper around the popular **QuillJS** editor.

It allows users to write and format content in a way similar to word processors (e.g., bold, italic, lists, images, links) and outputs content as **HTML** or **Delta JSON**.

---

## 📚 Table of Contents

1. [Why use React Quill?](#-why-use-react-quill)
2. [Features](#️-features)
3. [Example - Basic Usage](#-example--basic-usage)
4. [Toolbar Customization](#️-toolbar-customization)
5. [Output Format](#-output-format)
    - [Delta JSON](#-what-is-delta-json)
6. [Security Note](#-security-note)
7. [When Not to Use It](#-when-not-to-use-it)

---

## 🚀 Why Use React Quill?

React Quill is ideal when your application requires user-generated rich content, such as:

- ✅ Blog post editors
- ✅ Forum/comment sections
- ✅ CMS content editing
- ✅ Internal documentation tools
- ✅ Notes or descriptions with formatting

---

## ⚙️ Features

- Built-in formatting: bold, italic, underline, headers, lists, links, blockquotes, code blocks, etc.
- Outputs **HTML** or **Delta JSON** format
- Customizable toolbar
- Controlled component: integrates naturally with React state
- Pluggable and extensible

---

## 🧪 Example – Basic Usage

```tsx
import { useState } from 'react';
import ReactQuill from 'react-quill';

export default function MyEditor() {
  const [value, setValue] = useState('');

  return (
    <div>
      <h2>Rich Text Editor</h2>
      <ReactQuill theme="snow" value={value} onChange={setValue} />
      <h3>HTML Output:</h3>
      <div style={{ border: '1px solid #ccc', padding: '10px' }}>
        {value}
      </div>
    </div>
  );
}
```

### 💡 Notes

- `value` contains the editor content in HTML.
- You can store it in your database as a string and render it later with `dangerouslySetInnerHTML`.

---

## 🛠️ Toolbar Customization

You can define your own toolbar layout using the `modules` prop:

```ts
const modules = {
  toolbar: [
    [{ header: [1, 2, 3, false] }],
    ['bold', 'italic', 'underline', 'strike'],
    [{ list: 'ordered' }, { list: 'bullet' }],
    ['link', 'blockquote', 'code-block'],
    ['clean'],
  ],
};
```

Use it like this:

```tsx
<ReactQuill
  value={value}
  onChange={setValue}
  modules={modules}
  theme="snow"
/>
```

---

## 🧾 Output Format

By default, React Quill returns HTML. You can also access the Quill instance to work with **Delta** (Quill's internal rich format):

```tsx
const quillRef = useRef<ReactQuill | null>(null);

const getDelta = () => {
  const editor = quillRef.current?.getEditor();
  const delta = editor?.getContents(); // returns Delta format
  console.log(delta);
};
```

### 📐 What Is Delta JSON?

A **Delta** is a JSON array of operations, where each operation represents an insert, delete, or retain action, along with optional formatting.

#### Delta vs HTML Example

Imagine the user writes:

> Hello **world**

The resulting HTML would be:

```html
<p>Hello <strong>world</strong></p>
```

The equivalent **Delta** JSON would be:

```json
[
  { "insert": "Hello " },
  { "insert": "world", "attributes": { "bold": true } },
  { "insert": "\n" }
]
```

This format:

- Keeps text and formatting **separate**
- Prevents **malicious HTML**
- Allows full control over operations and transformations

---

## 🛡 Security Note

- **React Quill returns raw HTML**, so be careful when rendering it.
- Always sanitize HTML output using libraries like `DOMPurify` before injecting it into the DOM.

---

## 📚 When Not to Use It

React Quill is **not ideal** if:

- You need markdown editing
- You want a plain text-only input
- You need a highly customized editor not easily supported by QuillJS
