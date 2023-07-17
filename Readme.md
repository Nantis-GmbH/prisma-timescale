# Timescale Prisma Issues

The timescale extension is correctly recognized and put into the migration correctly.

When running prisma migration commands such as `prisma migrate dev` or `prisma migrate deploy` the following error is thrown:

```
    Migration `20230717062750_init` failed to apply cleanly to the shadow database.
Error:
db error: ERROR: extension "timescaledb" has already been loaded with another version
DETAIL: The loaded version is "2.11.1".
HINT: Start a new session and execute CREATE EXTENSION as the first command. Make sure to pass the "-X" flag to psql.
   0: schema_core::state::EvaluateDataLoss
             at schema-engine\core\src\state.rs:315
```

# Steps to reproduce
1. Run the `npm install` command
1. Create two services on [Timescale Cloud](https://console.cloud.timescale.com/signup) one for the main database and one for the shadow.
1. Add the database urls to the .env file
1. Run the `prisma migrate dev` command