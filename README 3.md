# README 3 — Guided SQL Learning Tasks

## Learning Mini Project — London Transport SQL Insights in Databricks

---

## 1. Purpose of this README

This README is the main SQL learning section of the mini project.

The goal now is to move from “I found the dataset” to “I can query it correctly and deliberately inside Databricks.”

You will work in the **SQL Editor**, which Databricks uses for writing, running, managing, and sharing queries. The current editor supports autocomplete, multi-statement queries, saved drafts, result panes, and visualizations. ([Databricks Documentation][1])

This README is intentionally **click-by-click**.
Each task tells you:

* where to click
* what SQL to type
* what to expect
* what the step means technically

---

## 2. Before you begin

You should already have these from README 2:

* the full table name
* a few useful column names
* an idea of the likely business measure
* an idea of which columns could be used for grouping or filtering

For the examples below, I will use placeholder names like:

```sql
catalog_name.schema_name.table_name
```

and sample columns such as:

```sql
station_id
station_name
line_name
journey_count
journey_date
region
```

Replace those with the real names from your dataset.

A useful Databricks detail to keep in mind: a **fully qualified table name** overrides the catalog and schema selectors in the SQL Editor, so it is often the safest beginner approach. ([Databricks Documentation][1])

---

## 3. Step 1 — Open the SQL Editor and confirm compute

### Click path

1. In the left sidebar, click **SQL Editor**.
2. Look near the top of the editor for the **SQL warehouse** selector.

Databricks says you must have at least **CAN USE** permission on a SQL warehouse to run queries. If you have a default warehouse, the SQL Editor uses it automatically; otherwise you choose one from the list. The selected warehouse can also restart automatically when you run a query. ([Databricks Documentation][1])

### What to do

* If a warehouse is already selected, keep it.
* If no warehouse is selected, click the warehouse selector and choose the one your trainer told you to use.

### What this means

The SQL Editor is your authoring surface.
The SQL warehouse is the compute engine that executes your SQL.

---

## 4. Step 2 — Open a fresh query tab

### Click path

1. In the SQL Editor, look for the **+** at the top of the query tabs.
2. Click **+**.
3. Choose **Create new query**.

Databricks documents that the current SQL Editor uses tabs and lets you open a new tab with **+**, then **Create new query** or **Open existing query**. ([Databricks Documentation][1])

### What you should expect to see

A fresh SQL editing area.

Databricks notes that new queries are automatically named **New query** with a timestamp and are created in your Drafts area until you save or rename them. ([Databricks Documentation][1])

### What this means

You are now working in a clean query authoring context.

---

## 5. Step 3 — Run your first controlled preview query

### Type this

Replace the placeholder with your real table name:

```sql
SELECT *
FROM catalog_name.schema_name.table_name
LIMIT 10;
```

### Then do this

1. Click inside the query editor.
2. Click **Run** near the top of the SQL Editor.

Databricks documents that to run a query, you select a SQL warehouse and then click **Run** or use `Ctrl/Cmd + Enter`. The current SQL Editor also supports multi-statement queries, where each statement ends with a semicolon. ([Databricks Documentation][1])

### What you should expect to see

A result table with a small set of rows.

### What this means

This is not yet analysis.
This is a controlled verification step:

* the table is reachable
* the SQL warehouse is working
* the query path is working
* the dataset structure is visible in the query result

---

## 6. Step 4 — Narrow the query to selected columns

### Why this step exists

`SELECT *` is useful for a first preview, but it is not the normal working pattern for careful SQL analysis. Real query work usually selects only the columns needed for the task.

### Type this

Replace the names with columns from your dataset:

```sql
SELECT
  station_id,
  line_name,
  journey_count
FROM catalog_name.schema_name.table_name
LIMIT 10;
```

### Then do this

1. Click anywhere in the query.
2. Click **Run** again.

### What you should expect to see

A smaller, cleaner result table with only the selected columns.

### What this means

You are now controlling the shape of the output instead of taking the whole table.
That is the first real move from data preview toward analysis.

---

## 7. Step 5 — Use filtering with `WHERE`

### Why this step exists

Filtering is how you reduce a larger dataset to the subset that actually matters for a question.

### Type this

Use a real condition based on your data. Example:

```sql
SELECT
  station_id,
  line_name,
  journey_count
FROM catalog_name.schema_name.table_name
WHERE journey_count > 10000
LIMIT 10;
```

### Then do this

1. Highlight the query if you have more than one statement in the editor.
2. Click **Run**.

Databricks notes that if you have multiple statements in one tab, you can highlight the one you want to run. ([Databricks Documentation][1])

### What you should expect to see

Only rows that satisfy the condition.

### What this means

You are no longer only reading the data.
You are applying logic to reduce the data to a meaningful subset.

---

## 8. Step 6 — Use sorting with `ORDER BY`

### Why this step exists

Sorting helps you see extremes, rankings, and patterns quickly.

### Type this

```sql
SELECT
  station_id,
  line_name,
  journey_count
FROM catalog_name.schema_name.table_name
ORDER BY journey_count DESC
LIMIT 10;
```

### Then do this

1. Click **Run**.

### What you should expect to see

The highest journey counts first.

### What this means

This is now a ranking-style query.
You are using SQL not just to retrieve records, but to organize them in a way that answers a business question.

---

## 9. Step 7 — Combine filtering and sorting

### Why this step exists

Real query work usually combines multiple operations, not just one.

### Type this

```sql
SELECT
  station_id,
  line_name,
  journey_count
FROM catalog_name.schema_name.table_name
WHERE journey_count > 10000
ORDER BY journey_count DESC
LIMIT 10;
```

### Then do this

1. Click **Run**.

### What you should expect to see

A filtered and ranked subset.

### What this means

This is closer to real reporting logic:
first restrict the population,
then order the result for easier interpretation.

---

## 10. Step 8 — Group records with `GROUP BY`

### Why this step exists

Grouping is how you move from row-level data to summarized information.

### Type this

```sql
SELECT
  line_name,
  COUNT(*) AS row_count
FROM catalog_name.schema_name.table_name
GROUP BY line_name
ORDER BY row_count DESC;
```

### Then do this

1. Click **Run**.

### What you should expect to see

One row per `line_name`, plus a count for each group.

### What this means

You are no longer reading individual records.
You are producing a grouped summary.

This is one of the most important changes in SQL thinking:
from raw rows to aggregated structure.

---

## 11. Step 9 — Use `SUM` for a business measure

### Why this step exists

A count tells you how many records exist.
A sum tells you the total value of a metric.

### Type this

```sql
SELECT
  line_name,
  SUM(journey_count) AS total_journeys
FROM catalog_name.schema_name.table_name
GROUP BY line_name
ORDER BY total_journeys DESC;
```

### Then do this

1. Click **Run**.

### What you should expect to see

One row per line, with total journeys per line.

### What this means

This is a more meaningful business summary than raw row counts when `journey_count` is your real measure.

---

## 12. Step 10 — Use aliases clearly

### Why this step exists

Alias names make outputs easier to read and easier to reuse in later visuals.

### What to notice

In the last query, these are aliases:

```sql
COUNT(*) AS row_count
SUM(journey_count) AS total_journeys
```

### Why this matters

Without aliases, result columns often have technical names that are harder to interpret.
With aliases, the result becomes more presentation-ready.

This matters later when you convert the query result into a visual.

---

## 13. Step 11 — Use the SQL Editor helpers intelligently

Databricks’ current SQL Editor supports **autocomplete** while you type, including table aliases and columns, and it also lets you browse data objects in the left pane. ([Databricks Documentation][1])

### What to do

While typing a query:

1. Start typing a table name or alias reference.
2. Watch the autocomplete suggestions.
3. Use them if they help you avoid typing mistakes.

### What this means

This is not a shortcut for understanding SQL.
It is a productivity tool that reduces naming errors and speeds up authoring.

---

## 14. Step 12 — Save your first useful query

### Why this step exists

A useful query should not remain only as an unsaved draft.
In real work, good query logic is something you keep, organize, and reuse.

Databricks states that in the new SQL Editor, query content is continuously autosaved, and the **Save** button controls whether draft content is applied to related assets. Databricks also notes that new draft queries are created in your home directory until they are saved or renamed. ([Databricks Documentation][1])

### What to do

After running a useful query:

1. Look for the query title near the top.
2. Rename the query to something meaningful.

Suggested name:

```text
01_total_journeys_by_line
```

3. Use **Save** if your trainer wants the query explicitly saved and named for reuse.

### What this means

The query now becomes a reusable project asset rather than a temporary experiment.

---

## 15. Step 13 — Create a second saved query

### Why this step exists

The Day 5 project expects at least two saved queries.

### Suggested second query

Use a different question from the first one.

Example:

```sql
SELECT
  station_id,
  line_name,
  journey_count
FROM catalog_name.schema_name.table_name
ORDER BY journey_count DESC
LIMIT 10;
```

Suggested query name:

```text
02_top_stations_or_rows_by_journeys
```

### What to do

1. Open a new query tab with **+**.
2. Click **Create new query**.
3. Type the second query.
4. Click **Run**.
5. Rename and save it clearly.

Databricks supports multiple query tabs in the same SQL Editor session. ([Databricks Documentation][1])

### What this means

You are now building a small library of useful project queries.

---

## 16. Step 14 — Use multi-statement execution carefully

The current SQL Editor supports **multi-statement queries** if you separate statements with semicolons. Databricks also documents that by default the editor may run all statements unless you change that behavior. ([Databricks Documentation][1])

### Example pattern

```sql
SELECT
  line_name,
  SUM(journey_count) AS total_journeys
FROM catalog_name.schema_name.table_name
GROUP BY line_name
ORDER BY total_journeys DESC;

SELECT
  station_id,
  line_name,
  journey_count
FROM catalog_name.schema_name.table_name
ORDER BY journey_count DESC
LIMIT 10;
```

### Practical caution

For this project, keep your saved queries simple and separate unless your trainer explicitly wants multi-statement use.

### Why this matters

Beginners usually work more clearly when each saved query answers one main question.

---

## 17. Step 15 — Read the result like an engineer

After each query, stop and ask:

* What business question did this query answer?
* Did the result shape match the SQL logic?
* Is the measure meaningful?
* Is the grouping correct?
* Would this result be useful in a visual or dashboard later?

This is important because query writing is not only syntax work.
It is logic work.

A query is successful only when the output structure actually matches the question.

---

## 18. Recommended query progression for this project

By the time you finish README 3, try to have worked through at least this progression:

1. preview query with `SELECT *` and `LIMIT`
2. selected columns only
3. filtered result with `WHERE`
4. sorted result with `ORDER BY`
5. grouped count with `GROUP BY` and `COUNT`
6. grouped measure summary with `GROUP BY` and `SUM`
7. two clearly saved queries

That progression is deliberate.
It moves from inspection to control, then from control to summary.

---

## 19. What you should have by the end of this README

You should now have:

* a working SQL warehouse selected
* at least several successful query runs
* practice with:

  * `SELECT`
  * column selection
  * `LIMIT`
  * `WHERE`
  * `ORDER BY`
  * `GROUP BY`
  * `COUNT`
  * `SUM`
  * aliases
* at least two saved query assets

That is enough to move into visuals and dashboard work.

---

## 20. Clear takeaway

This README was the point where the project became real SQL work.

You did not just open the editor and type random queries.
You used the Databricks SQL Editor to move through the normal analysis path:

**preview data, control columns, filter rows, sort results, aggregate measures, and save useful query logic.**

That is the correct foundation for the next stage.

---

## Next step

Continue to **README 4 — Visuals and Dashboard Tasks**.

That file will show you how to take the queries you created here and turn them into:

* visual outputs
* reusable presentation views
* a simple dashboard inside Databricks

[1]: https://docs.databricks.com/aws/en/sql/user/sql-editor/ "Write queries and explore data in the new SQL editor | Databricks on AWS"
