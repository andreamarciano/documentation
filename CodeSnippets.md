# Automating VS Code Snippets for Repetitive Components

## 📝 What is a snippet?

A **snippet** in Visual Studio Code is a reusable code template that can be inserted quickly into your files by typing a prefix and hitting `Tab`. This is extremely useful when you have repetitive structures in your project.

For example, in a recipe app, each recipe page often uses the same layout components:

- `RecipeTitle`
- `IngredientsList`
- `ProcedureSteps`
- `ToolsList`
- `RecipeFootnotes`
- `UserComments`

---

## 📚 Table of Contents

1. [Manual snippet setup (quick method)](#-manual-snippet-setup-quick-method)
2. [Automating snippet management](#-automating-snippet-management)
    - [Step 1. Initialize scripts project](#-step-1-initialize-scripts-project)
    - [Step 2. Example `package.json`](#-step-2-example-packagejson)
    - [Step 3. Example `tsconfig.json`](#️-step-3-example-tsconfigjson)
    - [Step 4. `sync-snippets.ts` script](#-step-4-sync-snippetsts-script)
    - [Usage](#-usage)
    - [Example snippet file](#-example-snippet-file)

---

## ⚡ Manual snippet setup (quick method)

1. Press `Ctrl+Shift+P`
2. Type `Preferences: Configure User Snippets`.
3. Choose `typescriptreact` (if working with .tsx files).
4. Write your snippet JSON definition.

> ✅ We will show the snippet code example later in this guide.

---

## 🤖 Automating snippet management

When your project grows, maintaining many snippets manually becomes cumbersome. You may want to:

- Store snippet JSON files directly in your project (e.g. in `.vscode/snippets/`)
- Automatically sync them to VS Code's global user snippets folder

---

### 📂 Project structure

```text
/root
├── /.vscode
│    └── /snippets
├── /snippets
│    └── sync-snippets.ts
├── /backend
└── /frontend
```

---

### 🔧 Step 1. Initialize scripts project

Inside your `/snippets` folder, run:

```bash
npm init -y
npm install -D typescript ts-node @types/node
npx tsc --init
```

---

### 📝 Step 2. Example `package.json`

```json
{
  "name": "snippets",
  "version": "1.0.0",
  "description": "npm run snippets",
  "main": "index.js",
  "scripts": {
    "snippets": "ts-node sync-snippets.ts"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "type": "commonjs",
  "devDependencies": {
    "@types/node": "^24.0.10",
    "ts-node": "^10.9.2",
    "typescript": "^5.8.3"
  }
}
```

---

### ⚙️ Step 3. Example `tsconfig.json`

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "CommonJS",
    "esModuleInterop": true,
    "moduleResolution": "node",
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "skipLibCheck": true
  }
}
```

---

### 🔄 Step 4. `sync-snippets.ts` script

This script reads all snippet `.json` files in `.vscode/snippets/` and merges them into your VS Code user snippet file (`typescriptreact.json`).

```ts
import fs from "fs";
import path from "path";

const SNIPPETS_DIR = path.join(__dirname, "../.vscode/snippets");

function getVSCodeSnippetsPath() {
  return path.join(
    process.env.APPDATA!,
    "Code",
    "User",
    "snippets",
    "typescriptreact.json"
  );
}

// Read all snippets
function loadAllSnippets() {
  const files = fs.readdirSync(SNIPPETS_DIR);
  const allSnippets: Record<string, any> = {};

  for (const file of files) {
    if (file.endsWith(".json")) {
      const content = fs.readFileSync(path.join(SNIPPETS_DIR, file), "utf-8");
      const parsed = JSON.parse(content);

      // Merge snippets, checking for duplicates
      for (const [key, value] of Object.entries(parsed)) {
        if (allSnippets[key]) {
          console.warn(`Snippet duplicate key detected: ${key}`);
        }
        allSnippets[key] = value;
      }
    }
  }

  return allSnippets;
}

// Write to VS Code user snippets
function syncSnippets() {
  const targetPath = getVSCodeSnippetsPath();
  const snippets = loadAllSnippets();

  fs.writeFileSync(targetPath, JSON.stringify(snippets, null, 2), "utf-8");
  console.log(
    `✅ Synced ${Object.keys(snippets).length} snippets to ${targetPath}`
  );
}

syncSnippets();
```

---

### 💡 Usage

1. Place your snippet `.json` files in:

    ```text
    .vscode/snippets/
    ```

2. Run the script from the `/scripts` folder:

    ```bash
    npm run snippets
    ```

---

### 🔍 Example snippet file

Here is an example snippet JSON (`recipelayout.json`) for a recipe layout:

```json
{
  "Recipe Component Template": {
    "prefix": "recipelayout",
    "body": [
      "import {",
      "  RecipeTitle,",
      "  IngredientsList,",
      "  ProcedureSteps,",
      "  ToolsList,",
      "  RecipeFootnotes,",
      "  SectionWrapper,",
      "} from \"../_Utils/RecipeUtils\";",
      "import UserComments from \"../_Utils/RecipeComments\";",
      "import { useRecipeTranslation } from \"../_Utils/useRecipeTranslation\";",
      "import { useRecipeData } from \"../_Utils/useRecipeData\";",
      "",
      "export default function ${1:RecipeName}() {",
      "  const { title, ingredients, steps, footnotes, tools } = useRecipeTranslation(",
      "    \"pages/recipes/${2:category}/${3:recipeSlug}\"",
      "  );",
      "",
      "  const { slug, recipe, user, favoriteRecipes, setFavoriteRecipes } =",
      "    useRecipeData();",
      "  if (!slug || !recipe) return <p>Recipe not found</p>;",
      "",
      "  return (",
      "    <article className=\"mx-auto px-3 my-4\" style={{ maxWidth: 750 }}>",
      "      <RecipeTitle",
      "        recipeId={recipe.id}",
      "        user={user}",
      "        favoriteRecipes={favoriteRecipes}",
      "        setFavoriteRecipes={setFavoriteRecipes}",
      "      >",
      "        {title}",
      "      </RecipeTitle>",
      "",
      "      <SectionWrapper>",
      "        <IngredientsList ingredients={ingredients} />",
      "      </SectionWrapper>",
      "",
      "      <SectionWrapper>",
      "        <ProcedureSteps steps={steps} />",
      "      </SectionWrapper>",
      "",
      "      <SectionWrapper>",
      "        <ToolsList tools={tools} />",
      "      </SectionWrapper>",
      "",
      "      <SectionWrapper>",
      "        <RecipeFootnotes>",
      "          {footnotes.map((note, i) => (",
      "            <div key={i} dangerouslySetInnerHTML={{ __html: note }} />",
      "          ))}",
      "        </RecipeFootnotes>",
      "      </SectionWrapper>",
      "",
      "      <SectionWrapper>",
      "        <UserComments recipeId={recipe.id} />",
      "      </SectionWrapper>",
      "    </article>",
      "  );",
      "}"
    ],
    "description": "Recipe basic layout"
  }
}
```
