---
id: Notes
aliases: []
tags: []
---

[Golang-Migrate](https://github.com/golang-migrate/migrate.git): Golang tool to apply migrations

### What does migration mean ?

Migration refers to a set of changes made to the structure of a database over time. These changes are typically applied in a controlled and repeatable manner, ensuring that the database's schema remains consistent and reliable.

Golang-migrate uses a versioned migration approach, where each migration is assigned a unique identifier or version number. This allows the tool to track the order in which migrations should be applied, ensuring that the database's schema evolves smoothly without conflicts or disruptions.

Each migration typically consists of two separate files:

- Up: This file contains the SQL statements that define the changes to be made to the database schema. These changes can include creating new tables, adding columns, modifying existing structures, or removing obsolete elements.
- Down: This file contains the SQL statements that reverse the changes made in the up file. This allows for easy rollback if any issues arise during the migration process.

By using golang-migrate, developers can manage database migrations in a structured and predictable manner, ensuring that their applications have a consistent and reliable data layer. This helps to maintain the integrity and stability of their applications over time, even as the database schema evolves with the application's requirements.

#### _Command to apply migrations_:

`migrate -path <path-to-migrations-files> -database "<database-connection-link>" -verbose <up/down>`

#### `Up` and `Down` migrations file

The up file contains the database codes to create tables. The down file contains code to drop the table

`<file-identifier>.up.sql`

```sql
CREATE TABLE "users" (
  "id" BIGSERIAL PRIMARY KEY,
  "username" VARCHAR NOT NULL,
  "email" VARCHAR NOT NULL,
  "password" VARCHAR NOT NULL
);
```

`<file-identifier>.down.sql`

```sql
DROP TABLE IF EXISTS "users";
```

Command to create migration files.

```zsh
migrate create -ext sql -dir <directory-to-place-migration-files> <file-name>
```
