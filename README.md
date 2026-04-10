# README 1 — Project Overview and Business Scenario

## Learning Mini Project — London Transport SQL Insights in Databricks

---

## 1. Project purpose

This mini project is designed to teach **Databricks SQL Editor and dashboards** through a small, realistic workflow.

You will not start with abstract SQL theory.
You will start with a real platform task:

**use Databricks to inspect data, write SQL queries, save useful query logic, create visuals, and assemble a simple dashboard.**

Databricks’ current SQL workflow centers on the **SQL editor** for authoring and running queries, managing saved queries, browsing available data, and creating visualizations. Databricks also supports built-in visualization and dashboard creation directly from SQL results. ([Databricks Documentation][1])

---

## 2. Business scenario

You are working as a junior data practitioner in a transport analytics setting.

A small London Transport dataset is already available in Databricks.
Your job is to turn that raw table into something operationally useful.

The questions are simple, but real:

* Which stations or lines appear most active?
* How can we filter and sort the data quickly?
* How can we summarize journeys in a form a business user can read?
* How can we turn query results into visuals and then into a lightweight dashboard?

This is not yet a large analytics solution.
It is the smallest realistic version of the workflow teams use every day:

**data → query → saved logic → visual output → dashboard view**

---

## 3. What this project will teach

By the end of this mini project, your work should show that you can:

* navigate to the SQL working area in Databricks
* identify the dataset you will query
* open the SQL editor
* write and run basic SQL queries
* refine queries using filtering, sorting, grouping, and aggregation
* save useful queries
* turn query results into visuals
* place visuals into a dashboard-style output

Databricks’ current SQL editor supports writing, running, saving, and sharing queries, while built-in visualizations can be created directly from SQL query results. ([Databricks Documentation][1])

---

## 4. What you will produce

At the end of this mini project, you should have:

* one identified London Transport dataset
* multiple working SQL queries
* at least two saved queries
* one or two visual outputs
* one simple dashboard
* short written observations about what the results show

This matches the normal Databricks SQL workflow: query authoring, saved queries, visual generation, and dashboard assembly. ([Databricks Documentation][1])

---

## 5. How the project is organized

This mini project is split into five README files.

### README 1 — Project Overview and Business Scenario

This file explains the project goal, scenario, workflow, and outputs.

### README 2 — Databricks Setup and Project Start

This file will show you exactly where to click to enter the correct SQL work area, locate the dataset, and start the project in the right place.

### README 3 — Guided SQL Learning Tasks

This file will take you through SQL work step by step in the SQL editor.

### README 4 — Visuals and Dashboard Tasks

This file will show you how to turn saved query results into visuals and then into a simple dashboard.

### README 5 — Reflection, Wrap-Up, and Final Deliverables

This file will close the project and help you verify what you built.

---

## 6. Working style for this project

This project uses a very specific learning style.

Each practical section is written so that you can:

1. see **where to click**
2. perform the step in Databricks
3. understand what the step means
4. understand why that step belongs in the workflow

So this project is not just conceptual.
It is intentionally written as a **guided hands-on execution path**.

That matters because Databricks is a working platform.
The goal is not only to know what a SQL editor or dashboard is.
The goal is to be able to move through the platform correctly and use it in the right sequence.

---

## 7. Platform context

This project is designed to work as closely as possible to a **Databricks Free Edition / free-tier style** experience.

The SQL work will be based around the current **Databricks SQL editor** and dashboard workflow. Databricks currently documents the **new SQL editor** as the main interface for writing queries, exploring data, and creating visualizations, and Databricks has announced that the new SQL editor will become the default for all workspaces starting in late May 2026, with legacy editor retirement planned for late July 2026. ([Databricks Documentation][1])

That means the steps in this project are aligned to the **current direction of the product**, not older UI assumptions. ([Databricks Documentation][1])

---

## 8. Real engineering logic behind this project

This project is small, but the workflow is real.

The engineering logic is:

* first identify the data source correctly
* then query it in a controlled way
* then save useful logic instead of rewriting everything repeatedly
* then produce visual outputs from those queries
* then present the result in a dashboard form that another person can consume

That is why the project is structured in this order.

A dashboard without controlled queries underneath it is weak.
A query without understanding the data source is weak.
A result that is not saved or organized is difficult to reuse.

So the point of this project is not just “write some SQL.”
The point is to perform a small but correct **analytics workflow inside Databricks**.

---

## 9. Before you begin

Before moving to README 2, make sure you are clear on the following:

* this is a **Databricks SQL learning project**
* the dataset will already exist or be provided in the workspace context
* you will work through the platform step by step
* later readmes will be more operational and more click-by-click
* you should expect to create both **queries** and **presentation outputs**

---

## 10. Clear takeaway

This project is about learning how Databricks SQL work actually happens in practice:

**find data, query it, save useful logic, visualize it, and present it clearly.**

That is the working model you should keep in mind as you move into README 2.

---

## Next step

Open **README 2 — Databricks Setup and Project Start**. It will begin the practical work and show exactly where to click to enter the SQL workflow correctly.

[1]: https://docs.databricks.com/aws/en/sql/user/sql-editor/ "Write queries and explore data in the new SQL editor"
