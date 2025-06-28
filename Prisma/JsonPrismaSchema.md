# Prisma Models → JSON Schema & Type Validation

In modern TypeScript fullstack applications, consistency between database models, API request validation, and frontend typing is essential. Prisma handles the database layer, but it doesn't validate incoming API data. To ensure type-safe, validated inputs across the stack, many teams adopt a pattern where they derive:

1. **JSON Schemas** from Prisma models — for API documentation, validation, and type sharing
2. **Zod/Ajv validators** — to ensure API request payloads conform to expectations

---

## 📚 Table of Contents

1. [Why Generate JSON Schemas and Validators?](#why-generate-json-schemas-and-validators)
2. [Key Concepts](#key-concepts)  
   - [JSON Schema](#1-json-schema)  
   - [Zod (TypeScript Runtime Validation)](#2-zod-typescript-runtime-validation)
3. [General Implementation Flow](#general-implementation-flow)  
   - [Step 1: Define Prisma Model](#-step-1-define-prisma-model)  
   - [Step 2: Create Zod Validator](#-step-2-create-zod-validator-manually-or-automatically)  
   - [Step 3: Use in Routes](#-step-3-use-in-routes-eg-express)  
   - [Step 4: Export JSON Schema](#-step-4-optional-export-json-schema)

---

## Why Generate JSON Schemas and Validators?

- **API Consistency**: Ensure backend routes accept data that match your database model
- **Validation**: Catch malformed or incomplete data before it hits the DB
- **Type Reuse**: Share types across backend & frontend
- **Documentation**: JSON Schemas help generate OpenAPI specs or other docs automatically

---

## Key Concepts

### 1. JSON Schema

- A standard for describing the shape of JSON objects
- Used for **validation**, **documentation**, and **schema sharing**
- Tools like `ajv` or `express-json-validator` use JSON Schema to validate incoming requests

Example:

```json
{
  "type": "object",
  "properties": {
    "title": { "type": "string" },
    "published": { "type": "boolean", "default": false }
  },
  "required": ["title"]
}
```

### 2. Zod (TypeScript Runtime Validation)

Zod is a powerful validation library that lets you define schemas and get both:

- Compile-time type inference
- Runtime validation

Example:

```ts
import { z } from "zod";

const PostSchema = z.object({
  title: z.string(),
  published: z.boolean().optional().default(false),
});
```

---

## General Implementation Flow

### ✅ Step 1: Define Prisma Model

```prisma
model Post {
  id        String   @id @default(uuid())
  title     String
  published Boolean  @default(false)
  createdAt DateTime @default(now())
}
```

### ✅ Step 2: Create Zod Validator Manually or Automatically

**Manual:**

```ts
import { z } from "zod";

export const PostValidator = z.object({
  title: z.string(),
  published: z.boolean().optional(),
});
```

**Optional – Auto-generation:**
Use libraries like:

- `prisma-json-schema-generator`
- `zod-prisma`, `prisma-zod-generator`

These generate JSON Schemas or Zod schemas automatically from your Prisma schema.

### ✅ Step 3: Use in Routes (e.g. Express)

```ts
app.post("/api/posts", async (req, res) => {
  try {
    const data = PostValidator.parse(req.body); // throws if invalid
    const post = await prisma.post.create({ data });
    res.json(post);
  } catch (err) {
    res.status(400).json({ error: "Invalid input", details: err });
  }
});
```

### ✅ Step 4: (Optional) Export JSON Schema

If you're using Zod, you can convert your schema into JSON Schema:

```ts
import { zodToJsonSchema } from "zod-to-json-schema";

const jsonSchema = zodToJsonSchema(PostValidator, "Post");
```
