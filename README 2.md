# README 2 — Databricks Setup and Project Start

## Learning Mini Project — London Transport SQL Insights in Databricks

---

## 1. Purpose of this README

This README gets the project into the **correct working context**.

The goal here is not to write complex SQL yet.
The goal is to do the setup properly so that the rest of the project starts from the right place:

* enter the Databricks workspace
* open the **SQL Editor**
* identify the dataset you will query
* confirm the catalog, schema, and table you will work with
* verify that you can preview data before writing the main queries

Databricks’ current SQL workflow is centered on the **SQL Editor**, which is used to author queries, browse available data, and create visualizations. The **Catalog** area is the standard place to explore catalogs, schemas, tables, and sample data. ([Databricks Documentation][1])

---

## 2. Before you start

You should already have:

* access to a Databricks workspace
* a provided London Transport dataset, or instructions from the trainer on which dataset to use
* permission to view the relevant catalog, schema, and table

To explore objects in Catalog Explorer, Databricks says you need at least **BROWSE** privilege; to query with SQL, you need **SELECT** on the table plus **USE CATALOG** and **USE SCHEMA** on its parent objects. ([Databricks Documentation][2])

If your trainer already gave you a table name, keep it ready.
If not, this README will help you locate it.

---

## 3. What you are trying to find

By the end of this README, you should know the full name of the dataset you will use, ideally in this form:

```sql
catalog_name.schema_name.table_name
```

That matters because in Databricks, the SQL environment is organized around **catalogs**, **schemas**, and **tables/views**. Catalogs are the top-level container, schemas sit inside catalogs, and tables/views sit inside schemas. ([Databricks Documentation][2])

A simple mental model:

* **catalog** = top-level data domain
* **schema** = subdivision inside the catalog
* **table** = the actual data object you query

---

## 4. Step 1 — Enter the Databricks workspace

### What to do

1. Sign in to your Databricks workspace.
2. Wait until the main workspace interface is visible.
3. Look at the left-hand sidebar.

### What you should expect to see

You should see the main navigation area, including workspace navigation and, in current Databricks environments, a **SQL Editor** entry in the sidebar or in the “more” navigation area. Databricks documents the SQL Editor as a standard workspace UI entry. ([Databricks Documentation][1])

### What this means

You are not starting in notebooks for this project.
You are starting in the SQL workflow.

That is an important shift from Day 4.

---

## 5. Step 2 — Open the SQL Editor

### Click path

1. In the left sidebar, click **SQL Editor**.

### If you do not immediately see it

* look for a condensed sidebar
* expand the sidebar if needed
* look under additional navigation options if your workspace layout is compact

Databricks’ current documentation states directly: to open the SQL editor in the Databricks UI, click **SQL Editor** in the sidebar. ([Databricks Documentation][1])

### What you should expect to see

The SQL Editor will open either:

* to your last open query, or
* to the SQL Editor landing page if no query is already open. ([Databricks Documentation][1])

### What this means

This is now your main authoring surface for Day 5.

The SQL Editor is where you will:

* write SQL
* run SQL
* save SQL
* later create visuals from query results ([Databricks Documentation][1])

---

## 6. Step 3 — Make sure you are in the current SQL editor experience

### What to check

Look near the catalog and schema selectors in the SQL Editor.

Databricks currently documents a **new SQL editor** and explains that users may still see a toggle in some environments while the rollout completes. Databricks also states that the new SQL editor becomes the default in late May 2026 and the legacy editor is retired in late July 2026. ([Databricks Documentation][1])

### What to do

* If your workspace already opens in the current editor, continue.
* If you see a **New SQL editor** toggle and it is off, turn it on for your query if your trainer wants the current interface.

### What this means

For this project, the intended workflow is the **current SQL editor** workflow, not the older legacy editor flow. ([Databricks Documentation][1])

---

## 7. Step 4 — Identify where data exploration happens

You now need to find the London Transport dataset before writing the main project queries.

There are two useful places for this:

* **Catalog Explorer** for browsing objects visually
* **SQL Editor** for writing commands like `SHOW CATALOGS`, `SHOW SCHEMAS`, and `SHOW TABLES` ([Databricks Documentation][2])

For this project, start with **Catalog Explorer** because it gives the clearest click-by-click path.

---

## 8. Step 5 — Open Catalog Explorer

### Click path

1. In the left sidebar, click **Catalog**.

Databricks says: select the **Catalog** icon in the workspace sidebar to access Catalog Explorer. ([Databricks Documentation][2])

### What you should expect to see

You should see a data browsing interface where you can inspect:

* catalogs
* schemas
* tables
* views ([Databricks Documentation][2])

### What this means

Catalog Explorer is the platform’s structured data navigation layer.
This is where you confirm that the dataset exists before you start writing SQL against it.

---

## 9. Step 6 — Find the correct catalog

### Click path

1. In Catalog Explorer, look at the list of available catalogs.
2. Click the catalog your trainer told you to use.
3. If no catalog was specified, look for the one that contains your training dataset.

Databricks documents that Catalog Explorer shows the list of catalogs available to you, and clicking a catalog selects it. ([Databricks Documentation][2])

### What you should expect to see

After selecting a catalog, you should see the schemas inside that catalog. ([Databricks Documentation][2])

### What to record

Write down the catalog name somewhere visible.
You will need it later in SQL queries.

Example placeholder:

```text
transport_catalog
```

### What this means

You are choosing the top-level data namespace for the project.

---

## 10. Step 7 — Find the correct schema

### Click path

1. Inside the selected catalog, look at the list of schemas.
2. Click the schema that contains the transport dataset.

Databricks documents that when you select a catalog in Catalog Explorer, you see the available schemas, and clicking a schema selects it. ([Databricks Documentation][2])

### What you should expect to see

You should now see the data objects available in that schema, especially tables and views. ([Databricks Documentation][2])

### What to record

Write down the schema name.

Example placeholder:

```text
london_transport
```

### What this means

You have now narrowed the project to the specific data area that contains your dataset.

---

## 11. Step 8 — Find the table you will use

### Click path

1. Inside the selected schema, look for **Tables**.
2. Expand **Tables** if needed.
3. Click the table your trainer wants you to use.

Databricks notes that when you select a schema, you see the list of available tables and views, and you may need to click **Tables** to expand them if other object types are present. ([Databricks Documentation][2])

### What you should expect to see

When you select the table, you should be able to inspect details such as:

* columns
* sample data
* table details
* possibly history, if relevant and supported for that table ([Databricks Documentation][2])

### What to record

Write down the full dataset name:

```text
catalog_name.schema_name.table_name
```

Example placeholder:

```text
transport_catalog.london_transport.station_journeys
```

### What this means

This is now the central object for your mini project.
All later SQL work depends on identifying this object correctly.

---

## 12. Step 9 — Inspect the columns

### Click path

1. With the table selected, click the **Columns** tab.

Databricks documents that the **Columns** tab shows table columns in Catalog Explorer. ([Databricks Documentation][2])

### What you should expect to see

A list of column names and their data types.

### What to do

Look for columns that seem useful for the project.

For a London Transport-style dataset, examples might look like:

* `station_id`
* `station_name`
* `line_name`
* `journey_count`
* `date`
* `region`

Your actual columns may be different.

### What to record

Write down at least 3 to 5 columns that look important.

### Why this matters

You should not begin querying a table blindly.
Real SQL work starts with understanding the available fields and their likely business meaning.

---

## 13. Step 10 — Inspect sample data

### Click path

1. With the same table selected, click the **Sample Data** tab.

Databricks documents that the **Sample Data** tab lets you view sample records from a table, provided you have access to active compute where required. ([Databricks Documentation][2])

### What you should expect to see

You should see example rows from the table.

### What to do

Read the rows carefully and answer these practical questions:

* What does one row represent?
* Which column looks like the main business measure?
* Which columns look like dimensions for grouping or filtering?
* Does the data look station-level, line-level, time-based, or mixed?

### What to record

Write 2 or 3 short observations.

Example:

* One row appears to represent a station or station/date combination.
* `journey_count` appears to be the main metric.
* `line_name` looks useful for grouping.

### Why this matters

This is the point where the table stops being just a technical object and starts becoming a queryable business dataset.

---

## 14. Step 11 — Return to the SQL Editor

### Click path

1. Go back to the left sidebar.
2. Click **SQL Editor** again.

### What this means

You have now completed the data-identification part of the workflow.
Next, you are moving back into query authoring.

This is the correct sequence:

**find data first, then query it**

---

## 15. Step 12 — Create a fresh query

### What to do

If the SQL Editor is showing an existing query or landing page:

1. Open a new query tab or create a new query in the current editor.
2. Keep the editor focused on the dataset you just identified.

Databricks’ current SQL editor is the place to write, run, manage, and share queries. ([Databricks Documentation][1])

### What you should expect to see

A query editor surface with space to type SQL.

### What this means

You now have the correct authoring surface and the correct dataset context.

---

## 16. Step 13 — Set the data context explicitly

If your trainer wants fully qualified table names everywhere, you can always query using:

```sql
SELECT * 
FROM catalog_name.schema_name.table_name
LIMIT 10;
```

If you want to set context first, Databricks documents the use of `USE CATALOG` and `USE SCHEMA` to make a catalog and schema active. ([Databricks Documentation][2])

Example pattern:

```sql
USE CATALOG catalog_name;
USE SCHEMA schema_name;
```

Then:

```sql
SELECT * 
FROM table_name
LIMIT 10;
```

### What to do

Use whichever approach your trainer specifies.

### Recommended beginner choice

For this project, the safest beginner approach is usually the **fully qualified table name**, because it makes the source explicit.

### Why this matters

When learners are new to Databricks SQL, ambiguity about the active catalog/schema often causes confusion.
Being explicit removes that confusion.

---

## 17. Step 14 — Run a first preview query

### Type this pattern

Replace the placeholders with your real table name:

```sql
SELECT * 
FROM catalog_name.schema_name.table_name
LIMIT 10;
```

### Then do this

1. Click **Run**.

Databricks documents the SQL Editor as the place to author and run queries. ([Databricks Documentation][1])

### What you should expect to see

A result table with a small number of rows.

### What this means

This is your first proof that:

* you found the right dataset
* you have access to it
* the SQL workflow is working correctly
* the project can now move into guided SQL learning

---

## 18. Step 15 — Verify the project start is correct

Before moving on, confirm all of the following:

* you can open the **SQL Editor**
* you can open **Catalog Explorer**
* you identified the correct catalog
* you identified the correct schema
* you identified the correct table
* you reviewed columns
* you previewed sample data
* you ran a first SQL preview query successfully

If all of those are true, the setup is complete.

---

## 19. What to keep written down before README 3

You should now have these notes ready:

### Dataset identification

* catalog name
* schema name
* table name
* full table reference

### Field awareness

* at least 3 to 5 useful columns
* your best guess about the main measure
* your best guess about useful grouping/filtering columns

### Example template

```text
Catalog: ____________________
Schema: _____________________
Table: ______________________
Full name: __________________

Likely measure column: __________________
Useful grouping columns: ________________
Useful filtering columns: _______________
```

These notes will make the next README much easier.

---

## 20. Clear takeaway

This README was about starting the project correctly.

You did not begin with random SQL.
You first established:

* where SQL work happens
* where the data lives
* what table you will query
* what the data appears to mean

That is the correct engineering start for Databricks SQL work.

---

## Next step

Continue to **README 3 — Guided SQL Learning Tasks**.

That file will begin the actual SQL work step by step, including:

* `SELECT`
* choosing columns
* `LIMIT`
* `WHERE`
* `ORDER BY`
* `GROUP BY`
* `COUNT`
* `SUM`
* aliases
* saving useful queries

[1]: https://docs.databricks.com/aws/en/sql/user/sql-editor/ "Write queries and explore data in the new SQL editor | Databricks on AWS"
[2]: https://docs.databricks.com/aws/en/discover/database-objects "Explore database objects | Databricks on AWS"
