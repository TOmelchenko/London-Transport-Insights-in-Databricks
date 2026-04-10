# README 5 — Reflection, Wrap-Up, and Final Deliverables

## Learning Mini Project — London Transport SQL Insights in Databricks

---

## 1. Purpose of this README

This README closes the mini project properly.

The goal here is not to introduce a new tool.
The goal is to finish the work in a disciplined way:

* confirm what you built
* capture the final project outputs
* record a small amount of evidence
* explain the logic of your work clearly
* leave the project in a state that another person could review

By this point, the project should already contain the main working pieces:

* identified dataset
* SQL queries
* saved queries
* visual outputs
* a dashboard

This final README turns those pieces into a clean finished submission.

---

## 2. What you should already have before starting this README

Before working on this final README, make sure you already completed the earlier parts of the mini project.

You should have:

* access to the Databricks workspace
* one identified London Transport dataset
* at least two working SQL queries
* at least two clearly saved queries
* at least one visual
* one simple dashboard

If any of those are missing, go back and complete the earlier README files first.

---

## 3. Final project deliverables

Your final mini project submission should include the following:

### Core deliverables

* the name of the dataset you used
* at least two SQL queries you wrote
* at least two saved queries in Databricks
* at least one visual
* one simple dashboard

### Reflection deliverables

* short written observations about the query results
* a short explanation of the most useful SQL concept you used
* a short explanation of the main platform insight from the project

### Evidence deliverables

Include **2 to 3 screenshots** as evidence of completion:

1. **one screenshot of the SQL Editor** showing a useful query and its result
2. **one screenshot of a visual**
3. **one screenshot of the dashboard**

This is enough evidence for the project.
Do not create unnecessary screenshots for every small action.

---

## 4. Screenshot guidance

The screenshots should be clear and useful.

### Screenshot 1 — SQL Editor evidence

Capture:

* the SQL Editor
* the query text
* the result table underneath it

Try to choose one of your better queries, such as:

* total journeys by line
* top stations by journey count
* grouped summary by a useful category

### Screenshot 2 — Visualization evidence

Capture:

* one finished visual
* the chart title
* enough of the result or UI context to show it is your project output

### Screenshot 3 — Dashboard evidence

Capture:

* the dashboard title
* the visual components inside the dashboard
* enough of the layout to show it is a real dashboard view

### Practical rule

Do not over-document.
The screenshots are there to confirm completion, not to replace the actual work.

---

## 5. Step 1 — Confirm your saved queries

Go back into the SQL Editor and make sure your saved queries are clearly named.

### What to check

You should have at least two saved queries with meaningful names.

Examples:

* `01_total_journeys_by_line`
* `02_top_stations_by_journey_count`

### Why this matters

A saved query is not just a temporary result.
It is a reusable project asset.

If the query names are vague, the work becomes harder to review and harder to reuse later.

---

## 6. Step 2 — Confirm your visual outputs

Open your visual outputs and make sure they are still readable and correctly titled.

### What to check

For each visual, check:

* does the title match the query result?
* is the chart type appropriate for the result?
* does the output make sense without opening the SQL?

### Practical reading test

Ask yourself:

* if someone else opened this visual, would they understand what it shows?
* does the title explain the output clearly?
* is the visual easy to read quickly?

If the answer is no, fix the title or simplify the visual.

---

## 7. Step 3 — Confirm your dashboard

Open the dashboard and review it as a finished output.

### What to check

* is the dashboard title clear?
* does it contain the intended visual elements?
* is the layout simple and readable?
* do the visuals belong together logically?
* does the dashboard tell a small but coherent story?

### Example logic

A good simple dashboard might look like this:

* one grouped summary chart
* one top-N supporting view
* one short title or heading

That is enough for this project.

---

## 8. Step 4 — Record the dataset details

Write down the dataset you used.

Use this template:

```text
Catalog: workspace
Schema:  london_transport
Table:   transport_activity
Full name: workspace.london_transport.transport_activity
```

### Why this matters

A project should identify its source clearly.

Without that, the SQL work is harder to interpret and harder to reproduce.

---

## 9. Step 5 — Record your final query list

List the main queries you created.

Use this template:

```text
Query 1 title: 01_total_journeys_by_line
Purpose: Calculate total passengers per transport line, ordered from busiest to least busy.

Query 2 title: 02_top_stations_by_journeys
Purpose: Find the top 10 stations by total passenger count, with a secondary count of total journey records per station.
```

### What this does

This step makes the logic of your project visible.

The project is not only “some SQL was written.”
It should be clear what each query was trying to answer.

---

## 10. Step 6 — Write short observations from the results

Now write **short result observations**.

- The first query grouped all journeys by line and showed that passenger volume is unevenly distributed — some lines carry significantly more passengers than others.
- `COALESCE` was used in both queries to handle missing values — stations or lines with no name were labeled as `Unknown` instead of being dropped from the results.
- The second query limited results to the top 10 stations, which made it easier to focus on the highest-traffic locations rather than reading through the full dataset.
- Comparing `total_passengers` and `total_journeys` side by side in query 2 revealed that some stations have high passenger counts but fewer individual journey records, suggesting those stations serve longer or busier routes.
- The bar and line combo chart in query 2 made it easier to spot stations where journey count and passenger count behave differently.


---

## 11. Step 7 — Identify the most useful SQL concept in this project

`GROUP BY` was the most useful concept in this project. Both queries used it to collapse raw journey-level rows into summary-level results — grouping by `line_name` in the first query and by `station_name` in the second. Without `GROUP BY`, the result would have been one row per journey record, which is too granular to interpret. With it, the data became comparable across lines and stations. Combined with `SUM` and `COUNT`, it turned a flat table into meaningful operational insight.

---

## 12. Step 8 — Identify the main platform insight

The main platform insight was that Databricks SQL is a structured workflow, not just a place to run ad hoc queries. The SQL Editor allowed queries to be written, run, and saved as reusable named assets. Those saved queries then became the source for visuals, and the visuals were assembled into a dashboard — all within the same platform. The key realization was that each step builds on the previous one: the table feeds the query, the query feeds the visual, and the visual feeds the dashboard. Working inside Databricks made that sequence explicit and repeatable.

---

## 13. Step 9 — Add your screenshot evidence

Now gather the final screenshots.

### Required evidence set

Include:

* **Screenshot A:** SQL Editor with one query and its result
* **Screenshot B:** one visual
* **Screenshot C:** the dashboard

### Submission rule

Keep the screenshots clean and relevant.

Do not submit:

* blurred captures
* screenshots that do not show the actual work clearly
* too many repeated screenshots of the same thing

The goal is to show the key project outputs clearly.

---

## 14. Step 10 — Perform a final self-check

Use this checklist before you finish.

### Final checklist

* I identified the dataset clearly.
* I know the catalog, schema, and table name.
* I created at least two SQL queries.
* I saved at least two queries with meaningful names.
* I created at least one visual.
* I created one dashboard.
* I wrote short observations about the results.
* I identified the most useful SQL concept.
* I identified the main Databricks platform insight.
* I collected 2 to 3 screenshots as evidence.

If all of these are true, the mini project is complete.

---

## 15. Final reflection prompt

The workflow started by locating the `transport_activity` table inside the `workspace.london_transport` schema in the Databricks catalog. The SQL Editor was used to write and run two queries — one grouping passengers by line, one ranking the top 10 stations by passenger count. The queries used `GROUP BY`, `SUM`, `COUNT`, `COALESCE`, and `ORDER BY` to produce clean summary results. Each query was saved with a meaningful name so it could be reused and referenced later. Visuals were created directly from the query results — a bar chart for line totals and a combo bar and line chart for station comparisons. Those visuals were then added to a dashboard to present both views together in one place. The final step was reviewing the results and confirming the outputs made sense before closing the project.

---

## 16. What this project was really teaching

This project was not only about writing a few SQL statements.

It was teaching a small but realistic analytics workflow inside Databricks:

* identify the correct data
* query it deliberately
* save useful logic
* turn results into readable visuals
* assemble those visuals into a dashboard

That is the real operational model behind the mini project.

---

## 17. Clear takeaway

By the end of this mini project, you should be able to describe Databricks SQL work in a practical way:

**find the data, query it, save the useful logic, visualize the results, and present them through a dashboard.**

That is the main Day 5 outcome.

---

## 18. End of project

You have now completed:

**Learning Mini Project — London Transport SQL Insights in Databricks**

Your final submission should contain:

* dataset identification
* saved queries
* visual output
* dashboard
* written observations
* reflection answers
* 2 to 3 screenshots

This closes the Day 5 mini project.
