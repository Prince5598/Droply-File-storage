# Drizzle Setup Guide

## Prerequisites
- Node.js and npm installed
- PostgreSQL database (Neon)
- ImageKit account

## 1. Install Dependencies
```bash
npm install drizzle-orm @neondatabase/serverless
npm install -D drizzle-kit
```

## 2. Database Schema
Create `lib/db/schema.ts`:
```typescript
import { pgTable, text, timestamp, boolean, integer } from "drizzle-orm/pg-core";
import { createId } from "@paralleldrive/cuid2";

export const files = pgTable("files", {
  id: text("id").primaryKey().$defaultFn(() => createId()),
  name: text("name").notNull(),
  path: text("path").notNull(),
  size: integer("size").notNull(),
  type: text("type").notNull(),
  fileUrl: text("file_url"),
  thumbnailUrl: text("thumbnail_url"),
  userId: text("user_id").notNull(),
  parentId: text("parent_id"),
  isFolder: boolean("is_folder").default(false),
  isStarred: boolean("is_starred").default(false),
  isTrash: boolean("is_trash").default(false),
  createdAt: timestamp("created_at").defaultNow(),
  updatedAt: timestamp("updated_at").defaultNow(),
});
```

## 3. Database Connection
Create `lib/db/index.ts`:
```typescript
import { drizzle } from "drizzle-orm/neon-http";
import { neon } from "@neondatabase/serverless";
import * as schema from "./schema";

const sql = neon(process.env.DATABASE_URL!);
export const db = drizzle(sql, { schema });
```

## 4. Drizzle Configuration
Create `drizzle.config.ts` in the root directory:
```typescript
import type { Config } from "drizzle-kit";

export default {
  schema: "./lib/db/schema.ts",
  out: "./drizzle",
  driver: "pg",
  dbCredentials: {
    connectionString: process.env.DATABASE_URL!,
  },
} satisfies Config;
```

## 5. Environment Setup
Add to your `.env` file:
```env
DATABASE_URL="your-postgres-connection-string"
```

## 6. NPM Scripts
Add to your `package.json`:
```json
{
  "scripts": {
    "db:generate": "drizzle-kit generate:pg",
    "db:push": "drizzle-kit push:pg",
    "db:studio": "drizzle-kit studio"
  }
}
```

## 7. Initialize Database
Run these commands:
```bash
npm run db:generate  # Generate migrations
npm run db:push     # Push schema to database
```
