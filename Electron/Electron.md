# 🖥️ Introduction to Electron – Build Desktop Apps with Web Technologies

**Electron** is a framework that allows developers to build **cross-platform desktop applications** using **web technologies** like HTML, CSS, and JavaScript. It combines **Chromium** (the browser engine behind Chrome) with **Node.js**, giving you the power to build desktop apps using the same tools you’d use for a web app.

---

## 📚 Table of Contents

1. [How Electron Works](#-how-electron-works)
2. [Key Features](#key-features)
3. [Processes in Electron](#processes-in-electron)
4. [Simple Example](#simple-example)
5. [Common Use Cases](#-common-use-cases)
6. [Pros and Cons](#️-pros-and-cons)

---

## 🔧 How Electron Works

Electron essentially bundles:

- A **Chromium browser**: to render your UI using HTML/CSS/JavaScript
- A **Node.js runtime**: to interact with the local filesystem, OS, and other native APIs

This means your app is essentially a web app that runs in a native window with extra powers.

---

## Key Features

- **Cross-platform**: Build once, run on Windows, macOS, and Linux
- **Access to native APIs**: Use Node.js modules to interact with files, OS, clipboard, etc.
- **Full control over window and system behavior**
- **Auto-updates**, **notifications**, and **native menus** support
- **Easy packaging** and distribution using tools like `electron-builder` or `electron-forge`

---

## Processes in Electron

| Process         | Description |
|-----------------|-------------|
| **Main Process** | Starts Electron, creates windows, manages native OS functions |
| **Renderer Process** | Runs inside Chromium (one per window) – like a browser tab |
| **Preload Script** | (Optional) A bridge to safely expose Node.js APIs to the frontend |

---

## Simple Example

Let’s build a basic desktop app that shows “Hello, Electron!” in a window.

### 1. `package.json`

```json
{
  "name": "hello-electron",
  "main": "main.js",
  "scripts": {
    "start": "electron ."
  },
  "devDependencies": {
    "electron": "^28.0.0"
  }
}
```

Install Electron:

```bash
npm install --save-dev electron
```

---

### 2. `main.js`

```js
const { app, BrowserWindow } = require('electron');
const path = require('path');

function createWindow() {
  const win = new BrowserWindow({
    width: 800,
    height: 600,
  });

  win.loadFile('index.html');
}

app.whenReady().then(createWindow);
```

---

### 3. `index.html`

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello Electron</title>
  </head>
  <body>
    <h1>Hello, Electron! 🚀</h1>
  </body>
</html>
```

---

### Run the App

```bash
npm start
```

This opens a native desktop window running your HTML UI.

---

## 🧩 Common Use Cases

- Code editors (e.g. **Visual Studio Code**)
- Communication apps (e.g. **Slack**, **Discord**)
- Dev tools (e.g. **Postman**)
- Markdown/Note apps (e.g. **Obsidian**)

---

## ⚖️ Pros and Cons

| Pros                            | Cons                                 |
| ------------------------------- | ------------------------------------ |
| Cross-platform                  | App size is large (Chromium + Node)  |
| Web dev stack (HTML/CSS/JS)     | Higher memory usage than native apps |
| Access to native APIs (Node.js) | Security must be handled manually    |
| Huge community and ecosystem    | No mobile support                    |
