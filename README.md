# Celestial Bodies Database

## Overview

This project is a PostgreSQL relational database developed as part of the [freeCodeCamp](https://www.freecodecamp.org/) Relational Database curriculum. It stores information about celestial bodies, including galaxies, stars, planets, moons, and planet types.

The project demonstrates database creation, table design, primary and foreign keys, data types, constraints, and relationships between tables.

## Technologies Used

- **PostgreSQL** — Relational database management system
- **SQL** — Database definition, data insertion, and querying
- **Bash** — Terminal interaction and database backup commands

## Database Structure

The database is named `universe` and contains five tables:

| Table | Description |
|---|---|
| `galaxy` | Stores galaxy names, types, ages, distances, and physical characteristics. |
| `star` | Stores information about stars and their associated galaxies. |
| `planet` | Stores planet names, types, ages, and associated stars. |
| `moon` | Stores moon names, radii, physical characteristics, and associated planets. |
| `planet_types` | Stores planet classifications and their descriptions. |

### Relationships

The database uses foreign keys to maintain referential integrity:

- One galaxy can contain multiple stars.
- One star can have multiple planets.
- One planet can have multiple moons.

These relationships connect the tables and help maintain consistent data.

## Database Features

- Automatically incrementing primary keys using `SERIAL`.
- Foreign key constraints to establish relationships between tables.
- `NOT NULL` constraints to require essential values.
- `UNIQUE` constraints to prevent duplicate names.
- Multiple PostgreSQL data types, including `VARCHAR`, `TEXT`, `INT`, `NUMERIC`, and `BOOLEAN`.
- SQL queries for retrieving and verifying stored information.
- Database backup using `pg_dump`.

## Getting Started

### 1. Create the database

Connect to PostgreSQL from your terminal:

```bash
psql --username=freecodecamp --dbname=postgres
```

Create the database:

```sql
CREATE DATABASE universe;
```

Connect to the database:

```sql
\c universe
```

### 2. Create the tables and insert data

Execute the SQL statements in the project to create the five tables, define their relationships, and populate them with sample records.

Insert data into the parent tables before the dependent tables to satisfy foreign key constraints.

### 3. Verify the database

List all tables:

```sql
\dt
```

Check the number of records in a table:

```sql
SELECT COUNT(*) FROM galaxy;
```

Retrieve planets and their moons:

```sql
SELECT planet.name AS planet, moon.name AS moon
FROM planet
JOIN moon USING (planet_id);
```

Retrieve stars and their galaxies:

```sql
SELECT star.name AS star, galaxy.name AS galaxy
FROM star
JOIN galaxy USING (galaxy_id);
```

## Database Backup

To save the database to an SQL dump file, exit `psql`:

```sql
\q
```

Run the following command in your Bash terminal:

```bash
pg_dump -cC --inserts -U freecodecamp universe > universe.sql
```

The resulting `universe.sql` file contains SQL statements for recreating the database and its data.

## Learning Outcomes

Through this project, I practised:

- Creating and managing PostgreSQL databases.
- Designing relational database schemas.
- Defining primary keys and foreign key relationships.
- Applying constraints to maintain data integrity.
- Working with different SQL data types.
- Inserting, retrieving, and joining relational data.
- Backing up databases using PostgreSQL command-line tools.

## Project Status

Completed as a learning project for the freeCodeCamp Relational Database curriculum. Final completion is subject to passing all free
