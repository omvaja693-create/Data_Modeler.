# 🚀 Data Modeler: Building a Normalized Star Schema Data Model

This project is an advanced Power BI assignment focused solely on **Data Modeling, ETL, and Schema Design**. The core objective was to build a robust, well-structured relational data model from normalized source data, demonstrating expertise in table relationships, cardinality, and standard Star/Snowflake schema implementation.

---

## 🎯 Project Objective

The goal of this task was to create an efficient and scalable data model in Power BI using Power Query and the Model View only. No calculated columns, DAX, or visual charts (other than the required verification Matrix table) were used.

The project specifically addressed:
* Table relationships and cardinality (1:Many, Many:1, and 1:1).
* Star vs. Snowflake schema design.
* Handling inactive/ambiguous paths and bidirectional filters.
* Defining data formats, categories, and hierarchies.

---

## 📁 Dataset Overview

The model was constructed from six source Excel files, transformed and cleaned via **Power Query**.

| File Name | Role | Key Fields |
| :--- | :--- | :--- |
| `Sales_Fact.xlsx` | **Central Fact Table** | `SalesID (PK)`, `CustomerID (FK)`, `ProductID (FK)`, `RegionID (FK)`, `DateKey (FK)` |
| `Customer_Dim.xlsx` | Dimension Table | `CustomerID (PK)` |
| `Product_Dim.xlsx` | Dimension Table | `ProductID (PK)` |
| `Region_Dim.xlsx` | Dimension Table | `RegionID (PK)` |
| `Date_Dim.xlsx` | Dimension Table | `DateKey (PK)` |
| `Returns_Fact.xlsx` | Fact or Snowflake Table | `ReturnID (PK)`, `SalesID (FK)`, `ReturnDateKey (FK)` |

---

## 🛠️ Key Project Tasks and Implementation Details

### 1. Data Transformation (Power Query)
* All files were imported and loaded via Power Query.
* Proper **data types** were applied (e.g., currency, whole numbers, dates).
* Blank rows were removed, and data was cleaned.

### 2. Schema and Relationship Design
* **Schema:** Implemented a **Star Schema** with `Sales_Fact` as the central table.
* **Returns Data:** The `Returns_Fact` was modeled as a second fact table, connected to `Sales_Fact` and `Date_Dim`.
* **Relationship Mapping:** Relationships were manually defined using Foreign and Primary keys:
    * `Sales_Fact` $\rightarrow$ `Customer_Dim`
    * `Sales_Fact` $\rightarrow$ `Product_Dim`
    * `Sales_Fact` $\rightarrow$ `Region_Dim`
    * `Sales_Fact` $\rightarrow$ `Date_Dim`
    * `Returns_Fact` $\rightarrow$ `Sales_Fact`
    * `Returns_Fact` $\rightarrow$ `Date_Dim` (Inactive relationship for `ReturnDateKey`)

### 3. Advanced Model Settings
* **Cardinality:** Appropriate relationship cardinalities were set (predominantly 1:Many).
* **Bidirectional Filters:** Bidirectional filters were enabled/disabled only where justified, with a preference for single-direction filters.
* **Inactive Relationships:** The secondary date path for returns (`Returns_Fact` $\rightarrow$ `Date_Dim` on `ReturnDateKey`) was intentionally set as an **inactive relationship** and simulated using the `Returns_Fact` table to handle specific inactive relationship scenarios.
* **Ambiguity:** Any remaining filter ambiguity issues were identified and resolved.

### 4. Data Enrichment
* **Data Categories:** Defined for proper sorting (e.g., City, Country, ProductName).
* **Hierarchies:** Built to support drill-down paths in the model:
    * `Date_Dim`: Year > Quarter > Month > Date
    * `Region_Dim`: Country > State > City
    * `Product_Dim`: Category > Subcategory > ProductName

---

## ✅ Verification Step

Model integrity and relationship flow were verified using the only allowed visual: a **Matrix Table**.

The Matrix table was used to verify:
* Sales grouped by Product Category and Region
* Return reasons by Fiscal Year
* Revenue by Customer Segment

---

## 📦 Deliverables

The project deliverables included:

* A single **`.pbix` file** containing the fully transformed model, relationships, hierarchies, and the verification Matrix table.
* A **short summary** (`.docx` or `.txt`) explaining:
    * The schema type chosen (Star/Snowflake).
    * Relationship rationale and filter flow.
    * Any issues encountered and how they were resolved.

---



