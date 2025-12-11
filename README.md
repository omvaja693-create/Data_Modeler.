# 📊 BI Data Model Construction & Schema Design Project 🛠️

## Project Overview

This repository documents the construction and enhancement of a robust, relational data model designed to support analytical reporting and business intelligence (BI) on Sales and Returns data. The core objective was to build a clean **Star Schema** with fully defined relationships, data quality standards, and built-in reporting hierarchies.

---

## 1. Data Ingestion and Preparation (Power Query)

The project began with ensuring a high quality of data integrity through comprehensive cleaning and transformation steps using Power Query.

* ✅ **Data Import:** All source files were successfully imported via Power Query.
* 🧹 **Data Cleansing:** Applied proper data types to all columns and removed blank rows, guaranteeing clean data input for the model.

## 2. Model Construction & Relationship Architecture

The data model was structured to support accurate filtering and calculations, adhering to best practices for data warehousing.

* ⭐ **Star Schema Design:** The model is centered around the `Sales_Fact` table, serving as the central fact table.
* 🔗 **Key Definition:** Primary Keys and Foreign Keys were manually defined to enforce referential integrity.
* 🔄 **Relationships Established:** Key relationships were created to link the central fact table to dimension tables:
    * `Sales_Fact` $\rightarrow$ `Customer_Dim`
    * `Sales_Fact` $\rightarrow$ `Product_Dim`
    * `Sales_Fact` $\rightarrow$ `Region_Dim`
    * `Sales_Fact` $\rightarrow$ `Date_Dim`
    * `Returns_Fact` $\rightarrow$ `Sales_Fact`
* ⚠️ **Inactive Relationship:** An inactive relationship was implemented for `Returns_Fact` $\rightarrow$ `Date_Dim` (specifically using the `ReturnDateKey`) to enable specific time-based calculations (e.g., measuring returns vs. sales across different date contexts).
* 🧭 **Filtering Logic:** Appropriate relationship cardinalities ($\text{1:Many}$) and cross-filter directions (preferring **Single**) were meticulously set to ensure data flows correctly. **Filter ambiguity issues** were identified and resolved.

## 3. Data Model Enhancements & Usability

The model was optimized for front-end reporting tools by adding organizational features and display formats.

* 🔢 **Data Formatting:** Set appropriate data formats across the model (e.g., currency, whole numbers, dates).
* 🏷️ **Data Categories:** Defined Data Categories (e.g., City, Country, ProductName) for better sorting and geo-mapping capabilities.
* 🌲 **Reporting Hierarchies Built:** Key organizational hierarchies were built into the Dimension tables to facilitate easy drill-down analysis:
    * **`Date_Dim`**: Year > Quarter > Month > Date
    * **`Region_Dim`**: Country > State > City
    * **`Product_Dim`**: Category > Subcategory > ProductName

## 4. Verification

A final verification step confirmed the accuracy and functionality of the established data model.

* ✅ **Model Validation:** A Matrix Table visual was used to successfully verify data flow and integrity across critical business axes:
    * Sales grouped by Product Category and Region.
    * Return reasons by Fiscal Year.
    * Revenue by Customer Segment.

---
