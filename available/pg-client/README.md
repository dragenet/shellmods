# pg-client

Adds the PostgreSQL client tools (libpq) to `$PATH`.

## What It Does

- Prepends the Homebrew-installed libpq binary directory to `$PATH`, making `psql`, `pg_dump`, and other client tools available without a full PostgreSQL server installation.

## Prerequisites

- libpq installed via Homebrew: `brew install libpq`.
