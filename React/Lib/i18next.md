# How to Implement Language Switching in React with i18next

This guide explains how to set up multilingual support in a React project using **i18next** and **react-i18next**, including dynamic loading of translation files and language detection.

---

## 📚 Table of Contents

1. [Installation](#1-installation)
2. [Project Structure for Translations](#2-project-structure-for-translations)
3. [Create the i18n Initialization File](#3-create-the-i18n-initialization-file)
4. [Import `i18n.ts` in Your Entry Point](#4-import-i18nts-in-your-entry-point)
5. [Using Translations in Components](#5-using-translations-in-components)
6. [Translating Rich Text with `<Trans>`](#translating-rich-text-with-trans)

---

## 1. Installation

Run the following command to install the necessary packages:

```bash
npm install i18next react-i18next i18next-http-backend i18next-browser-languagedetector
```

- **`i18next`**
  Core internationalization framework that handles translation loading, language switching, pluralization, and more.

- **`react-i18next`**
  React bindings for i18next. Provides the `useTranslation` hook and components like `<Trans>` for seamless integration in React.

- **`i18next-http-backend`**
  Backend plugin for loading translation files via HTTP (e.g., from the `public/locales` folder). Enables lazy loading of namespaces.

- **`i18next-browser-languagedetector`**
  Detects the user’s preferred language automatically (e.g., from browser settings, query string, localStorage).

---

## 2. Project Structure for Translations

Organize your translation JSON files inside the `public` folder as follows:

```text
public/
└── locales/
    ├── en/
    │   ├── common.json
    │   ├── navbar.json
    │   └── home.json
    └── it/
        ├── common.json
        ├── navbar.json
        └── home.json

```

Each JSON file contains key-value pairs for strings used in specific components or parts of the app.

Example:

`public/locales/en/navbar.json`

```json
{
  "login": "Sign In"
}
```

`public/locales/it/navbar.json`

```json
{
  "login": "Accedi"
}
```

---

## 3. Create the i18n Initialization File

Create a file `src/i18n.ts` to configure i18next with dynamic backend loading and language detection:

```ts
import i18n from "i18next";
import { initReactI18next } from "react-i18next";
import HttpBackend from "i18next-http-backend";
import LanguageDetector from "i18next-browser-languagedetector";

i18n
  .use(HttpBackend)
  .use(LanguageDetector)
  .use(initReactI18next)
  .init({
    fallbackLng: "en",
    supportedLngs: ["en", "it"],
    debug: true,
    backend: {
      loadPath: "/locales/{{lng}}/{{ns}}.json",
    },
    interpolation: {
      escapeValue: false,
    },
  });

export default i18n;
```

---

## 4. Import `i18n.ts` in Your Entry Point

In your main React entry file, import the `i18n.ts` file to initialize the i18next setup before rendering the app:

```ts
import "./i18n.ts";
```

---

## 5. Using Translations in Components

- Use the `useTranslation` hook from `react-i18next` inside any component to access translation strings.

- To change the language dynamically, use the `i18n.changeLanguage()` method, usually tied to buttons or dropdowns.

Example in `Navbar.tsx`:

```tsx
import { useTranslation } from "react-i18next";

function Navbar() {
  const { t, i18n } = useTranslation("navbar"); // specify namespace

  return (
    <nav>
      <button onClick={() => i18n.changeLanguage("en")}>EN</button>
      <button onClick={() => i18n.changeLanguage("it")}>IT</button>
      <button>{t("login")}</button>
    </nav>
  );
}

export default Navbar;
```

You can use multiple namespaces by calling `useTranslation("namespace")` with the appropriate JSON file name.

---

## Translating Rich Text with `<Trans>`

Sometimes you need to translate text that contains React elements like links, bold text, or other components inside the translation string. For this purpose, `react-i18next` provides the `<Trans>` component.

### When to use `<Trans>` vs `t()`

- Use `t()` for simple strings without embedded React components.
- Use `<Trans>` when the translated text includes HTML tags or React components that should be rendered.

### Example: Using `<Trans>` for rich text translation

```json
{
  "welcomeText": "Welcome to <strong>Recipes</strong>. Visit our <link>homepage</link>."
}
```

React component:

```tsx
import { Trans } from "react-i18next";

function WelcomeMessage() {
  return (
    <Trans i18nKey="welcomeText" components={{ strong: <strong />, link: <a href="/" /> }} />
  );
}
```

This will render:

**Welcome to *Recipes*. Visit our *homepage*.**

where `Recipes` is bold and `homepage` is a clickable link.
