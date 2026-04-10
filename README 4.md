# README 4 — Visuals and Dashboard Tasks

## Learning Mini Project — London Transport SQL Insights in Databricks

---

## 1. Purpose of this README

This README takes the SQL work you already created and turns it into **presentation-ready outputs**.

The workflow now changes from:

**write queries and inspect results**

to:

**select useful saved queries, create visual representations, and assemble a simple dashboard**

Databricks supports built-in visualizations directly from SQL query results in the SQL Editor, and current Databricks dashboard work is centered on **AI/BI dashboards**, which provide a canvas for visualizations, text, and filters. ([Databricks Documentation][1])

---

## 2. What you should already have

Before starting this README, you should already have:

* at least two working SQL queries
* at least two clearly named saved queries
* at least one grouped summary query
* at least one ranking or filtered query

A good pairing for this project is:

* **Query 1:** total journeys by line
* **Query 2:** top stations or top rows by journey count

Those two query shapes usually translate well into simple visuals such as bar charts and tables. Databricks supports multiple visualization types in the SQL Editor, including tables, bar charts, line charts, area charts, pie charts, maps, pivot-style outputs, and more. ([Databricks Documentation][1])

---

## 3. The practical goal of this README

By the end of this README, you should have:

* at least one saved visualization
* preferably a second visualization from a second saved query
* one simple dashboard that contains those visuals
* a dashboard layout that another person can read without opening the SQL itself

This matches the normal reporting flow Databricks documents for SQL and dashboards: query results can be visualized, and dashboards can then be used to share those insights in a cleaner form. ([Databricks Documentation][2])

---

## 4. Step 1 — Open a saved query in the SQL Editor

### Click path

1. In the left sidebar, click **SQL Editor**.
2. If your saved query is not already open, click the **+** at the top of the editor.
3. Choose **Open existing query**.
4. Select one of the queries you created in README 3.

Databricks documents tab-based query handling in the current SQL Editor, including creating a new query or opening an existing one from the **+** menu. ([Databricks Documentation][1])

### What you should expect to see

Your saved SQL query should open in a query tab, with the result either already visible from the last run or ready to be re-run.

### What this means

You are starting from an already useful query, not from raw data.
That is important because visuals should be built on top of **deliberate query logic**, not on top of accidental result sets.

---

## 5. Step 2 — Run the query again before creating a visual

### What to do

1. Click inside the query editor.
2. Click **Run**.

Databricks documents the SQL Editor as the place to author and run queries, and visualizations are created from query results. ([Databricks Documentation][1])

### What you should expect to see

The result grid should refresh with the latest output.

### Why this matters

Always create the visual from a **known current result**.
That keeps the visualization tied to a result you have just checked, not an older result you may no longer trust.

---

## 6. Step 3 — Decide what type of result you have

Before clicking into visualization options, classify the result:

* if the result is a **grouped summary**, a bar chart is often a good choice
* if the result is a **top-N list**, a bar chart or table often works well
* if the result is already highly tabular and detailed, a table may be the best visual
* if the result is time-based, a line chart may be better

Databricks provides multiple visualization types in the SQL Editor and separately documents the available chart types for notebook and SQL editor visualizations. ([Databricks Documentation][1])

### Recommended project choices

For this mini project, use simple visual choices:

* **Query 1: total journeys by line** → bar chart
* **Query 2: top stations / top rows by journeys** → table or bar chart

This keeps the project realistic and easy to interpret.

---

## 7. Step 4 — Create the first visualization from the query result

### Click path

1. Run the saved query.
2. In the result area, look for the visualization control.
3. Click the option to add or create a **Visualization**.

Databricks documents that visualizations can be created directly from SQL Editor results, and the platform’s SQL visualization tutorial uses query results as the starting point for creating charts. ([Databricks Documentation][1])

### What you should expect to see

A visualization editor or chart configuration panel.

### What this means

You are now moving from **query logic** to **result presentation**.

The important point is that the visualization is not independent.
It is attached to a specific query output.

---

## 8. Step 5 — Configure the first visual clearly

### Recommended first visual

Use your grouped summary query, for example:

```sql
SELECT
  line_name,
  SUM(journey_count) AS total_journeys
FROM catalog_name.schema_name.table_name
GROUP BY line_name
ORDER BY total_journeys DESC;
```

### Configuration logic

If you create a bar chart:

* category / x-axis: `line_name`
* value / y-axis: `total_journeys`

Databricks documents visualization editing in the SQL Editor and lists supported visualization types separately. ([Databricks Documentation][1])

### What to do

1. Choose a chart type such as **Bar**.
2. Map the grouping field to the category axis.
3. Map the numeric measure to the value axis.
4. Give the visual a clear title.

Suggested title:

```text
Total Journeys by Line
```

### Why this matters

A visual is only good if the chart structure matches the SQL structure.

A grouped categorical summary usually belongs in a categorical chart, not an arbitrary visual type.

---

## 9. Step 6 — Save the first visual

### What to do

After configuring the chart:

1. Save the visualization using a clear name.

Suggested name:

```text
01_total_journeys_by_line_chart
```

Databricks supports saving visualizations derived from query results and then using them in dashboard workflows. ([Databricks Documentation][2])

### What this means

The visual is now becoming a reusable asset rather than a temporary display.

---

## 10. Step 7 — Create a second visual from a different query

### What to do

1. Open your second saved query from README 3.
2. Click **Run**.
3. Create a second visualization from that query result.

### Recommended second query shapes

Option A:

```sql
SELECT
  station_id,
  line_name,
  journey_count
FROM catalog_name.schema_name.table_name
ORDER BY journey_count DESC
LIMIT 10;
```

Option B:

a grouped top-N summary if you created one.

### Recommended second visual

* **table**, if the result is record-oriented
* **bar chart**, if the result is clearly rankable and categorical

### Suggested visual title

```text
Top Journey Records
```

or

```text
Top Stations by Journey Count
```

### Why this matters

A dashboard is usually better when it combines more than one view of the data:

* one summary view
* one supporting detail or ranking view

That makes the dashboard more useful and less repetitive.

---

## 11. Step 8 — Keep the visualization logic simple

For this mini project, avoid overcomplicated visuals.

Do not try to use advanced chart types unless the data structure clearly requires them.

A strong beginner dashboard usually uses:

* bar chart
* table
* maybe a second bar chart

Databricks’ documentation emphasizes a broad visualization library, but a small project benefits more from correct chart selection than from maximum variety. ([Databricks Documentation][3])

### Good practical rule

Use the visual that makes the query result easiest to read, not the visual that looks most impressive.

---

## 12. Step 9 — Start a dashboard

Databricks’ current dashboard experience is built around **AI/BI dashboards**. Databricks describes these dashboards as an interactive visualization platform with a canvas-based editing model and sharable published views. ([Databricks Documentation][3])

### Click path

1. In the left sidebar, click **Dashboards**, if it is available in your workspace.
2. Click the option to create a new dashboard.

Databricks’ dashboard tutorial documents creating a dashboard in the UI and using a draft dashboard with **Canvas** and **Data** tabs. ([Databricks Documentation][4])

### What you should expect to see

A draft dashboard editor with a canvas area where widgets can be added.

### What this means

You are moving from isolated visuals to a single reporting surface.

---

## 13. Step 10 — Name the dashboard clearly

### What to do

Create the dashboard with a clear project name.

Suggested name:

```text
London Transport SQL Insights
```

### Why this matters

Dashboard names should describe the business view, not just the tool or lesson.

This makes the result easier to recognize later and easier to explain to someone else.

---

## 14. Step 11 — Add your first query result or visualization to the dashboard

Databricks’ current dashboard tutorial explains that a dashboard has a **Canvas** tab for widgets and a **Data** tab for the underlying datasets. Users can define datasets using SQL or by choosing a Unity Catalog table or view. ([Databricks Documentation][4])

For this project, keep the logic simple: use the SQL work you already built.

### What to do

Inside the dashboard:

1. Go to the dashboard editing area.
2. Add a dataset or query-backed visual.
3. Select your first saved SQL query or the data derived from it.
4. Add the corresponding visual to the canvas.

### What you should expect to see

A chart widget placed on the dashboard canvas.

### What this means

The dashboard is not storing random graphics.
It is presenting query-backed data widgets.

---

## 15. Step 12 — Add the second visual

### What to do

1. Add a second widget to the dashboard.
2. Use your second saved query or its result-based visual.
3. Place it beside or below the first widget.

### Practical layout suggestion

Use a simple two-widget layout:

* top or left: grouped summary chart
* bottom or right: supporting table or ranking view

### Why this matters

A small dashboard should still have structure.

One visual should answer the main question.
The second should add detail or supporting context.

---

## 16. Step 13 — Add a short text heading if available

AI/BI dashboards support canvas-based editing with dashboard widgets such as visualizations and text elements. Databricks describes the dashboard canvas as the editing area for widgets. ([Databricks Documentation][4])

### What to do

If your dashboard editor allows text elements:

1. Add a short text box or heading.
2. Use a simple title or subtitle.

Example:

```text
London Transport SQL Insights
Grouped journey totals and top activity results
```

### Why this matters

A dashboard becomes easier to read when it has a visible narrative frame, not just disconnected charts.

---

## 17. Step 14 — Read the dashboard like a business user

Now stop building for a moment and read the dashboard as if you were not the author.

Ask:

* Can I tell what the dashboard is about in a few seconds?
* Does the first chart answer a main question clearly?
* Does the second chart or table support the first one?
* Are the titles understandable without opening the SQL?
* Is the layout simple enough to read quickly?

Databricks describes dashboards as a way to transform data into sharable insights. That only works if the dashboard can be understood as a reporting surface, not just as an authoring artifact. ([Databricks Documentation][3])

---

## 18. Step 15 — Save the dashboard draft

### What to do

1. Save the dashboard draft.
2. Confirm the title is correct.
3. Make sure the widgets appear in the intended order.

Databricks documents draft dashboards as the editable state before publishing. ([Databricks Documentation][4])

### What this means

You now have a working dashboard artifact, even before any broader sharing or publishing decisions.

---

## 19. Optional step — Publish or share only if your environment allows it

Databricks states that published AI/BI dashboards can be shared more broadly inside the Databricks account, including with registered users who may not have workspace access. ([Databricks Documentation][3])

For this mini project, publishing is optional unless your trainer explicitly includes it.

### Why this is optional

The main learning target for Day 5 is:

* SQL editor
* saved queries
* visuals
* dashboard assembly

Publishing is useful, but it is not required for the basic project outcome.

---

## 20. What you should have by the end of this README

You should now have:

* at least one visualization built from a saved query
* preferably a second visualization
* one dashboard draft
* a dashboard name
* a readable dashboard layout
* a dashboard that connects clearly to the SQL work from README 3

That is enough to say you completed the visual-and-dashboard phase of the project.

---

## 21. Clear takeaway

This README was the point where SQL results became presentation outputs.

You did not just run queries and stop there.
You selected useful result sets, created visuals that match the query logic, and assembled those visuals into a small dashboard.

That is the core reporting workflow:

**saved query → visual → dashboard**

---

## Next step

Continue to **README 5 — Reflection, Wrap-Up, and Final Deliverables**.

That file will help you finish the mini project cleanly, verify what you built, and capture the main lessons from the full Day 5 workflow.

[1]: https://docs.databricks.com/aws/en/visualizations/ "Visualizations in Databricks notebooks and SQL editor"
[2]: https://docs.databricks.com/aws/en/sql/get-started/visualize-data-tutorial "Visualize queries and create a legacy dashboard"
[3]: https://docs.databricks.com/aws/en/dashboards/ "Dashboards | Databricks on AWS"
[4]: https://docs.databricks.com/aws/en/dashboards/tutorials/create-dashboard "Create a dashboard | Databricks on AWS"
