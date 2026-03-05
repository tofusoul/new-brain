
# Using DuckLake

DuckLake is a data lakehouse format that can be used with DuckDB. It allows you to manage large datasets while leveraging the speed and simplicity of DuckDB.

## Key Concepts

*   **Metadata Storage:** DuckLake stores metadata about your tables (schemas, versions, etc.) in a database. This can be a local DuckDB or SQLite file, or a remote database like PostgreSQL.
*   **Data Storage:** The actual data is stored in Parquet files in a separate directory.
*   **ACID Transactions:** DuckLake provides ACID guarantees for your data operations.
*   **Time Travel:** You can query previous versions of your tables.

## Creating a DuckLake

To create a DuckLake, you use the `ATTACH` command in DuckDB. The `ATTACH` command takes the path to the metadata file and the name you want to use for the lake.

**Example:**

```sql
-- Install and load the ducklake extension
INSTALL ducklake;
LOAD ducklake;

-- Attach a DuckLake with metadata stored in 'ducksoup/metadata.duckdb'
-- The data files will be stored in 'ducksoup/metadata.duckdb.files'
ATTACH '/path/to/your/data/ducksoup/metadata.duckdb' AS my_lake (TYPE DUCKLAKE);
```

## Working with Tables

Once the DuckLake is attached, you can create and query tables as you would with any other database.

**Example:**

```sql
-- Create a table
CREATE TABLE my_lake.my_table (id INTEGER, name VARCHAR);

-- Insert data
INSERT INTO my_lake.my_table VALUES (1, 'test');

-- Query data
SELECT * FROM my_lake.my_table;
```

## Time Travel

You can query a specific version of a table using the `AT (VERSION => ...)` syntax.

**Example:**

```sql
-- Query a specific version of a table
SELECT * FROM my_lake.my_table AT (VERSION => 1);
```
