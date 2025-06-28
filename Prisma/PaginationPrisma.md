# 📄 Pagination with Prisma Using `skip` and `take`

When querying large datasets, loading **all rows at once** is inefficient and unnecessary. Pagination is a common strategy to retrieve a **subset of records** — typically used in APIs and frontend applications.

Prisma makes pagination simple using the `skip` and `take` parameters in queries like `findMany`.

---

## 📚 Table of Contents

1. [How Pagination Works](#how-pagination-works)
2. [How to Calculate `skip`](#-how-to-calculate-skip)
3. [Adding Total Count](#-adding-total-count)
4. [Large datasets - Cursor-Based Pagination](#large-datasets---cursor-based-pagination)

---

## How Pagination Works

- `skip`: How many records to **skip**
- `take`: How many records to **retrieve**

This pattern allows you to implement **offset-based pagination** (the most common type).

### Example: Fetching Users Page by Page

Assume we have 100 users in the database.

#### ✅ Page 1 (First 10 users)

```ts
const usersPage1 = await prisma.user.findMany({
  skip: 0,
  take: 10,
});
```

#### ✅ Page 2 (Next 10 users)

```ts
const usersPage2 = await prisma.user.findMany({
  skip: 10,
  take: 10,
});
```

#### ✅ Page 3 (Third 10 users)

```ts
const usersPage3 = await prisma.user.findMany({
  skip: 20,
  take: 10,
});
```

---

## 🧮 How to Calculate `skip`

To calculate `skip`, use:

```ts
const skip = (currentPage - 1) * pageSize;
```

Where:

- `currentPage` is the page number (starting from 1)
- `pageSize` is how many items you want per page

### Example Function

```ts
async function getPaginatedUsers(page: number, pageSize: number) {
  const skip = (page - 1) * pageSize;

  return await prisma.user.findMany({
    skip,
    take: pageSize,
    orderBy: { createdAt: "desc" }, // optional
  });
}
```

> Use `orderBy` to ensure consistent results between pages (e.g. by `createdAt`)

---

## 📈 Adding Total Count

Often, you also want to return the **total number of items** to calculate how many pages exist:

```ts
const [total, users] = await Promise.all([
  prisma.user.count(), // total number of users
  prisma.user.findMany({
    skip: (page - 1) * pageSize,
    take: pageSize,
  }),
]);

const totalPages = Math.ceil(total / pageSize);
```

This is useful for frontend pagination UI (`Page 2 of 10`, etc.)

### ✅ API Response Example

```json
{
  "data": [/* 10 user objects */],
  "page": 2,
  "pageSize": 10,
  "total": 87,
  "totalPages": 9
}
```

---

## Large datasets - Cursor-Based Pagination

While offset-based pagination (`skip` + `take`) is simple and common, it has limitations in dynamic datasets (e.g. chat messages, social feeds) where records can change between requests very frequently (e.g. items being added or deleted).

### ❗ Problems with `skip`-based pagination

Imagine you're paginating posts sorted by date. If a new post is added or an old one is deleted between two client requests, the `skip` offset may become inaccurate, and the user might see **duplicated or skipped items**.

### ✅ Solution: Cursor-Based Pagination

Cursor-based pagination uses a **unique identifier** (typically `id`, `createdAt`, etc.) from the last fetched item as a *cursor*. The next page will start **after** that item.

This makes it more stable, especially in real-time or frequently updated systems.

### How It Works

- `cursor`: the point where the next page starts
- `take`: how many items to fetch
- `skip`: (optional) usually set to `1` to skip the cursor itself

---

### Example with Prisma

Imagine you already fetched the first 10 posts, and the last one had `id = 25`.  
To fetch the next page:

```ts
const posts = await prisma.post.findMany({
  cursor: { id: 25 }, // start after this post
  skip: 1,             // skip the post with id 25
  take: 10,
  orderBy: { id: "asc" },
});
```

#### Initial page (no cursor)

```ts
const firstPage = await prisma.post.findMany({
  take: 10,
  orderBy: { id: "asc" },
});
```

---

### Cursor-based Pagination Advantages

| Advantage                      | Description                                        |
| ------------------------------ | -------------------------------------------------- |
| ✅ More reliable                | Doesn’t break when records are inserted/deleted    |
| ✅ Stable ordering              | Based on a unique field (like `createdAt` or `id`) |
| ✅ Efficient for large datasets | No need to count or skip many rows                 |

### ⚠️ Limitations

| Limitation                   | Description                                                |
| ---------------------------- | ---------------------------------------------------------- |
| 🚫 No total count            | You can’t easily get `totalPages` or `pageNumber`          |
| 🚫 Can’t jump to page X      | You always go "forward" from the last cursor               |
| Needs consistent ordering | Must always use the same `orderBy` for predictable results |

### When to Use Which?

| Use Case                    | Recommended Pagination |
| --------------------------- | ---------------------- |
| Simple list, low traffic    | `skip` + `take`        |
| Admin dashboards            | `skip` + `take`        |
| Large datasets with updates | `cursor`-based         |
| Social feeds, chat messages | `cursor`-based         |
