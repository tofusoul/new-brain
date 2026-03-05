---
id: SurrealDB
aliases:
  - SurrealDB
tags: []
---

# SurrealDB

## IDs
- A **Record ID** has 2 parts, a table name and a record identifier. It looks like `table:record`. 
- Records are **Immutable**. You can't change them.
- When you `create table`, SurrealDB will assign a random ID. It is not an auto-incrementing id like in SQL.
- You can make explicit IDs by e.g. `CREATE product SET id = 'Surreal T-Shirt'`
- You can create an object based record ID by doing:
```SQL
 CREATE review: { product: 'Surreal T-Shirt', created_at: time::now()}
```
