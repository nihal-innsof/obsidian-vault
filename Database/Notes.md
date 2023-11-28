[Golang-Migrate](https://github.com/golang-migrate/migrate.git)

This tool allow us to create, apply, and rollback database changes in a controlled and repeatable way. This is important for maintaining the integrity and consistency of your database over time.

### What does migration mean ?
Migration refers to a set of changes made to the structure of a database over time. These changes are typically applied in a controlled and repeatable manner, ensuring that the database's schema remains consistent and reliable.

Golang-migrate uses a versioned migration approach, where each migration is assigned a unique identifier or version number. This allows the tool to track the order in which migrations should be applied, ensuring that the database's schema evolves smoothly without conflicts or disruptions.

Each migration typically consists of two separate files:
* Up: This file contains the SQL statements that define the changes to be made to the database schema. These changes can include creating new tables, adding columns, modifying existing structures, or removing obsolete elements.
* Down: This file contains the SQL statements that reverse the changes made in the up file. This allows for easy rollback if any issues arise during the migration process.

By using golang-migrate, developers can manage database migrations in a structured and predictable manner, ensuring that their applications have a consistent and reliable data layer. This helps to maintain the integrity and stability of their applications over time, even as the database schema evolves with the application's requirements.

#### *Command to apply migrations*:
`migrate -path <path-to-migrations-files> -database "<database-connection-link>" -verbose <up/down>`