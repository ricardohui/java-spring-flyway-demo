For concept, read https://www.baeldung.com/database-migrations-with-flyway

if you use spring boot default migration, place the sql in `src/main/resources`
if you use flyway to migrate, place the sql in `classpath(project root)/db/migration`
you have to enable mysql mode to support `ENGINE=InnoDB` in your schema.
https://stackoverflow.com/questions/58821490/spring-boot-2-2-1-h2-failures

The naming of your migration files should follow
<Prefix><Version>__<Description>.sql

Where:

<Prefix> – Default prefix is V, which may be configured in the above configuration file using the flyway.sqlMigrationPrefix property.
<Version> – Migration version number. Major and minor versions may be separated by an underscore. The migration version should always start with 1.
<Description> – Textual description of the migration. The description needs to be separated from the version numbers with a double underscore.
Example: `V1_1_0__my_first_migration.sql` 

Then run
```
mvn clean flyway:migrate -Dflyway.configFile=flyway.properties
```
