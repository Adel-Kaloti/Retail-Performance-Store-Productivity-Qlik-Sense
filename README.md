# Retail Performance & Store Productivity — Qlik Sense

> End-to-end Qlik Sense BI solution combining data engineering, executive reporting, interactive investigation, business storytelling, and data-quality validation.

![Main YTD Dashboard](Main%20YTD%20Dashboard.png)

---

## Project Overview

This project is an end-to-end **Retail Business Intelligence solution built in Qlik Sense**.

The solution was designed to move beyond static reporting and support three levels of analysis:

**Monitor → Investigate → Explain**

It combines:

- DB → ETL → UI architecture
- QVD-based data workflow
- validated Data Model
- comparable YTD analysis
- Executive Dashboard
- six investigation screens
- four analytical business stories
- Alternate State comparison
- geographic Store analysis
- Qlik Storytelling
- data-quality validation and analytical caveats

The goal is not only to show **what happened**, but to help identify **where it happened, what is driving it, and what management should investigate next**.

---

# Architecture

The solution follows a layered Qlik architecture:

```text
Source Data
     ↓
    DB
     ↓
    QVD
     ↓
    ETL
     ↓
Validated Data Model
     ↓
    UI
     ↓
Dashboards + Investigations + Stories
```

### DB Layer

Responsible for loading and preparing source data for reusable QVD storage.

### ETL Layer

Handles transformation, business rules, keys, data-quality logic, calculated fields, and preparation of the analytical model.

### UI Layer

Consumes the prepared data model and contains:

- KPIs
- dashboards
- investigation screens
- comparative analysis
- business storytelling

This architecture separates data preparation from presentation logic and makes the BI solution easier to validate and maintain.

---

# Data Model

![Qlik Data Model](Data%20Model.png)

The analytical model connects the major business entities required for:

- Sales
- Items
- Stores
- Calendar
- Inventory
- Goals
- Customers
- Employee-related analysis

Particular attention was given to:

- transaction-level keys
- date normalization
- comparable periods
- model relationships
- different business grains
- avoiding unnecessary synthetic-key problems

The Data Model was validated before the final analytical layer was built.

---

# Executive YTD Dashboard

![Main YTD Dashboard](Main%20YTD%20Dashboard.png)

The **Main YTD Dashboard** acts as the executive entry point to the solution.

It provides a fast view of:

- YTD Net Sales
- Sales Growth
- Net Quantity
- Average Price per Unit
- Goal performance
- Store contribution
- Salespeople performance
- Pareto concentration
- Department / Category mix
- Sales versus Volume behavior

One important high-level finding was that comparable YTD Sales increased while total Quantity remained almost flat.

This immediately raised the analytical question:

> **If Volume did not materially increase, what was driving the Sales growth?**

That question becomes one of the starting points for the investigation layer.

---

# Investigation Layer

The Executive Dashboard answers:

> **What is happening?**

The Investigation Screens are designed to answer:

> **Where is it happening, what is driving it, and which entity should we investigate next?**

The solution contains six dedicated investigation screens.

---

## 1. Sales Performance Investigation

![Sales Performance Investigation](Sales%20Performance%20Investigation.png)

Designed to identify unusual Store behavior across:

- Sales growth
- Quantity growth
- realized Price / Mix
- Price / Volume decomposition
- Goal Gap

This screen supports the transition from Network-level performance into specific Store-level anomalies.

---

## 2. Department, Category & Returns Investigation

![Department Category Returns Investigation](Department%2C%20Category%20%26%20Returns%20Investigation.png)

Provides deeper product-hierarchy analysis across:

- Departments
- Categories
- Sales
- Quantity
- recorded returns

The screen helps determine where performance changes and return activity are concentrated.

---

## 3. Store Goals & Performance Investigation

![Store Goals and Performance Investigation](Store%20Goals%20and%20Performance%20Investigation.png)

Focused on Store-level execution and performance against business targets.

The analysis includes:

- Goal achievement
- Goal Gap
- monthly Sales versus Goal
- transaction productivity
- performance drivers
- Department / Category concentration
- benchmark evidence

---

## 4. Item & Assortment Investigation

![Item and Assortment Investigation](Item%20%26%20Assortment%20Investigation.png)

Moves the investigation deeper into product and assortment behavior.

It supports analysis of:

- Store–Category mix
- sold assortment breadth
- Item productivity
- Item-level evidence
- SKU investigation candidates

This enables movement from aggregated patterns toward specific products that deserve review.

---

## 5. Inventory & Demand Investigation

![Inventory and Demand Investigation](Inventory%20%26%20Demand%20Investigation.png)

Connects current inventory exposure with recent and historical demand evidence.

The screen investigates:

- inventory allocation by Store
- Q1 positive demand
- inventory demand composition
- Collection exposure
- positive-demand history
- last-positive-sale recency
- Collection–Category combinations

---

## 6. Store Geography Investigation

![Store Geography Investigation](Store%20Geography%20Investigation.png)

Adds a geographic perspective to Store performance using latitude and longitude.

The screen combines geographic context with:

- Net Sales
- Net Quantity
- Return Value
- Return Rate

The map is used for broad geographic investigation and navigation.

Store coordinates are approximate and are **not used to claim precise distance, proximity effects, or cannibalization**.

---

# Analytical Story 1 — Growth Without Volume

## Business Question

Can strong Sales growth occur without meaningful Quantity growth?

A comparable YTD Store analysis identified **Las Vegas South Premium Outlets** as a strong growth outlier.

### Key Evidence

- Sales Growth: **+26.77%**
- Quantity Growth: **-1.03%**
- Realized Price / Mix: **+28.08%**

The Store generated materially higher Sales while total Quantity remained almost unchanged.

The investigation then moved through:

```text
Store Growth
    ↓
Sales vs Quantity vs Price/Mix
    ↓
Department Contribution
    ↓
Price / Volume Decomposition
    ↓
Item-Level Evidence
```

Ladies' Footwear explained approximately **97.7% of the Store's Sales increase**.

The decomposition showed that the largest component was the **Price Effect**, contributing approximately **₪70.6K**.

### Business Interpretation

The evidence indicates that the growth was primarily associated with **higher realized Price / Mix rather than higher Volume**.

### Management Direction

Investigate whether the stronger realized pricing / product mix is intentional, sustainable, and transferable to comparable Stores.

> The analysis does not claim that a specific Campaign caused the increase.

---

# Analytical Story 2 — Network Stability Hides Local Underperformance

## Business Question

Can acceptable Network-level performance hide a major Store-level Goal problem?

At Network level:

- Goal Achievement: **97.87%**
- Goal Gap: approximately **-₪675.7K**

However, **Camarillo** alone generated:

- Goal Achievement: **77.49%**
- Goal Gap: approximately **-₪579.9K**
- approximately **85.82%** of the Network net Goal Gap

The analytical path was:

```text
Network Goal Performance
    ↓
Goal Gap by Store
    ↓
Monthly Sales vs Goal
    ↓
Jul–Nov Performance Drivers
    ↓
Department Concentration
    ↓
Category Benchmark Evidence
```

During the critical July–November period:

- Sales: **-47.19%**
- Quantity: **-45.63%**
- Price / Mix: **-2.87%**

### Business Interpretation

Sales and Quantity deteriorated at very similar rates, while Price / Mix changed much less.

The strongest supported mechanism is therefore **Volume deterioration rather than a major pricing effect**.

### Management Direction

Prioritize a Store-level Volume investigation focused on the Departments and Categories responsible for most of the decline.

> Peer benchmarks are analytical comparison points, not proof of causation.

---

# Analytical Story 3 — Inventory & Demand Exposure

## Business Question

Is current inventory distributed consistently with recent Network demand?

The 31/03/2020 inventory snapshot revealed a major concentration at **Carlsbad**.

### Key Evidence

Carlsbad represented approximately:

- **47.77% of total Network Stock Value**

Within Carlsbad:

- approximately **78.95% of Stock Value** was associated with Items recording no positive Network Q1 demand

Carlsbad represented approximately:

- **74.82% of the Network's no-Q1-demand inventory exposure**

The investigation followed:

```text
Inventory Allocation
    ↓
Q1 Demand
    ↓
Demand Composition
    ↓
Historical Demand
    ↓
Collection Exposure
    ↓
Sale Recency
    ↓
Collection–Category Evidence
```

Three older Collections accounted for approximately **83.9%** of Carlsbad's no-Q1-demand Stock Value.

### Business Interpretation

The evidence supports a **current inventory-demand mismatch**.

However:

> No positive Q1 demand does not mean an Item never had demand.

Historical analysis showed that many of these Items recorded positive demand during 2019.

### Management Direction

Review the identified inventory groups for:

- allocation
- assortment decisions
- replenishment policy
- potential clearance review

> Stock is a snapshot at 31/03/2020. The analysis does not label this inventory automatically as obsolete or dead stock.

---

# Analytical Story 4 — Persistent Store–Category Mix Opportunity

## Business Question

Which Store–Category combinations consistently under-index relative to the Network product mix?

The Network-wide comparison identified:

> **Dolphin Mall × Covered**

as the leading persistent Mix Opportunity in both:

- 2019 Full Year
- 2020 Q1

### Q1 2020

- Dolphin Covered Sales Share: **42.88%**
- Network Covered Sales Share: **48.38%**
- Mix Index: **~0.886**
- Benchmark Mix Opportunity Gap: **~₪32K**

### 2019

- Mix Index: **~0.723**
- Benchmark Mix Opportunity Gap: **~₪195K**

The analytical path was:

```text
Network Store–Category Opportunities
    ↓
Dolphin Mall
    ↓
Covered
    ↓
Store Share vs Network Share
    ↓
Historical Persistence
    ↓
Sold Breadth vs Item Productivity
    ↓
SKU-Level Investigation
```

### Business Interpretation

The analysis compared two potential mechanisms:

1. Sold assortment breadth
2. Sales per active Item

Dolphin Mall showed a narrower active Covered assortment, while Sales per active Item remained much closer to comparable Store performance.

The strongest supported mechanism is therefore:

> **Narrower sold assortment breadth rather than unusually weak Item productivity.**

### Management Direction

Review Dolphin Mall's Covered assortment and investigate Network-proven SKUs that may deserve stronger local representation.

> The Mix Opportunity Gap is a benchmark scenario — not guaranteed Lost Sales.

---

# Advanced Qlik Capabilities

The project applies Qlik functionality to real analytical questions rather than using features only for demonstration.

Key capabilities include:

- **Qlik Sense**
- **Qlik Load Script**
- **QVD workflows**
- **Set Analysis**
- **Master Calendar**
- **Comparable YTD logic**
- **Alternate States**
- **Master Measures**
- **Drill-down analysis**
- **Price / Volume decomposition**
- **Pareto analysis**
- **Bullet Charts**
- **Scatter Plots**
- **Treemaps**
- **Maps**
- **KPI design**
- **Qlik Storytelling**

---

# Alternate State Comparison

The solution also includes a comparison screen built with **Qlik Alternate States**.

Alternate States allow two populations to maintain independent selection contexts inside the same Qlik application.

This enables side-by-side comparison of measures such as:

- recorded Employee / Manager Cost
- Sales
- Cost relative to Sales
- productivity-style measures

Employee-cost results are interpreted carefully because cost coverage in the source data is partial.

---

# Data Quality & Analytical Discipline

An important part of this project was identifying what the data **can** and **cannot** support.

## Comparable YTD

Period comparisons were aligned to comparable observed dates instead of blindly comparing unequal time periods.

## Transaction Identification

`DocumentNumber` could not safely be treated as a globally unique order identifier.

Transaction-level OrderKey logic was therefore validated separately.

## Inventory

Stock represents a snapshot rather than a complete historical inventory series.

The project therefore avoids unsupported historical stockout conclusions.

## Goals

Goal data contains known period and coverage limitations.

Goal-based analysis is presented with explicit comparison logic and assumptions.

## Campaigns

Campaign classification is incomplete.

Unclassified Sales are not automatically interpreted as confirmed “No Campaign” Sales.

## Employee Cost

Employee-cost and employee-metadata coverage are partial.

Cost measures therefore represent **available recorded cost**, not guaranteed complete labor cost.

## Geography

Coordinates are approximate and are used only for broad geographic investigation.

---

# Technology Stack

**Business Intelligence**
- Qlik Sense

**Data Engineering**
- Qlik Load Script
- QVD

**Analytics**
- Set Analysis
- KPI development
- YTD analysis
- benchmark analysis
- Price / Volume decomposition
- product-mix analysis
- Pareto analysis

**Validation**
- Data Model QA
- business-rule validation
- analytical consistency checks
- Python-assisted exploratory validation during development
