## 1. Extract nouns from the user stories or specification

```
As a food lover,
So I can stay organised and decide what to cook,
I'd like to keep a list of all my recipes with their names.

As a food lover,
So I can stay organised and decide what to cook,
I'd like to keep the average cooking time (in minutes) for each recipe.

As a food lover,
So I can stay organised and decide what to cook,
I'd like to give a rating to each of the recipes (from 1 to 5).

```

```
Nouns:
recipes
names
average cooking time (mins)
rating (1-5)
```

## 2. Infer the Table Name and Columns

Put the different nouns in this table. Replace the example with your own nouns.

| Record                | Properties          |
| --------------------- | ------------------- |
| recipe                 | name, cooking_time, rating |

Name of the table (always plural): `recipes`

Column names: `name`, `cooking time`,  `rating`

## 3. Decide the column types

[Here's a full documentation of PostgreSQL data types](https://www.postgresql.org/docs/current/datatype.html).

Most of the time, you'll need either `text`, `int`, `bigint`, `numeric`, or `boolean`. If you're in doubt, do some research or ask your peers.

Remember to **always** have the primary key `id` as a first column. Its type will always be `SERIAL`.

```
# EXAMPLE:

id: SERIAL
name: text
cooking_time: int
rating: smallint not null check (rating between 1 and 5)
```

## 4. Write the SQL

```sql
-- EXAMPLE
-- file: recipes_table.sql

-- Replace the table name, column names and types.

CREATE TABLE recipes (
  id SERIAL PRIMARY KEY,
  name text,
  cooking_time int,
  rating smallint not nill check (rating between 1 and 5)
);
```

## 5. Create the table

```bash
psql -h 127.0.0.1 recipe_directory < recipes_table.sql
```