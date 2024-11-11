# File Names

Versioned Migrations:

```
V2__
```

Versioned migrations have a version, a description, and a checksum. The version must be unique. The description is
purely informative so that you can remember what each migration does. The checksum is there to detect accidental
changes. Versioned migrations are the most common type of migration. They are applied in order exactly once. Optionally
their effect can be undone by supplying an undo migration with the same version.

Undo Migrations

```
U2__
```

Repetable Migrations

```
R__
```

Repeatable migrations have a description and a checksum, but no version. Instead of being run just once, they are (re-)
applied every time their checksum changes. Within a single migration run, repeatable migrations are always applied last,
after all pending versioned migrations have been executed. Repeatable migrations are applied in the alphanumeric order
of their description

# flyway_schema_history

See https://boottechnologies-ci.medium.com/database-migrations-in-a-spring-boot-application-using-flyway-399a9da29208

The flyway_schema_history table serves as a record of all migrations that have been applied to the database.
The flyway_schema_history table typically has the following columns:

installed_rank: The order in which the migration was applied.
version: The version number of the migration.
description: A brief description of the migration.
type: The type of migration (e.g., SQL, Java).
script: The name of the migration script.
checksum: A checksum of the migration script.
installed_by: The username of the user who applied the migration.
installed_on: The timestamp when the migration was applied.
execution_time: The time it took to execute the migration.
success: A boolean indicating whether the migration was successful.