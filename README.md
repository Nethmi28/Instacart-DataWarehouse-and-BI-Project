# 🛒 End-to-End Business Intelligence Pipeline — Instacart Grocery Dataset

> A complete data warehousing and analytics solution built on the Instacart Online Grocery Basket Dataset, demonstrating proficiency in dimensional modelling, ETL pipelines, OLAP analysis, and interactive dashboards.

---

## 📌 Project Summary

This project implements a full Business Intelligence lifecycle from raw data ingestion to executive-level reporting using industry-standard Microsoft data stack tools. It was designed to simulate a real world BI engineering workflow, covering data warehouse architecture, ETL development, multidimensional cube design, and interactive Power BI reporting.

**Key outcomes:**
- Designed and implemented a Snowflake schema data warehouse in SQL Server
- Built automated ETL pipelines using SSIS to load and transform multi-source data
- Developed an SSAS OLAP cube enabling multidimensional analysis
- Demonstrated five core OLAP operations: Roll Up, Drill Down, Slice, Dice, and Pivot
- Delivered four Power BI reports with advanced interactivity and drill-through capability

---

## 🗂️ Dataset

| Source | Description |
|--------|-------------|
| [Instacart Online Grocery Basket Dataset](https://www.kaggle.com/datasets/yasserh/instacart-online-grocery-basket-analysis-dataset) | Transaction-level grocery order data from Kaggle |
| [Mockaroo](https://www.mockaroo.com/) | Synthetically generated customer demographic data |

**Files used:** `Aisles.csv`, `Departments.txt`, `Products.csv`, `Ratings.txt`

---

## 🏗️ Data Warehouse Design

The warehouse follows a **Snowflake Schema**, chosen to reduce data redundancy across product hierarchy dimensions.

### Schema Diagram

```
                        ┌─────────────┐
                        │  DimDate    │
                        └──────┬──────┘
                               │
┌─────────────┐    ┌───────────▼──────────┐    ┌─────────────┐
│ DimCustomer │───▶│      FactOrder       │◀───│  DimRating  │
└─────────────┘    └──────────┬───────────┘    └─────────────┘
                              │
                    ┌─────────▼─────────┐
                    │    DimProduct     │
                    └────┬──────────────┘
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
        ┌──────────┐          ┌──────────────┐
        │ DimAisle │          │DimDepartment │
        └──────────┘          └──────────────┘
```

### Tables

| Table | Type | Description |
|-------|------|-------------|
| `FactOrder` | Fact | Central fact table capturing order-level transactions |
| `DimCustomer` | Dimension | Customer demographics from Mockaroo |
| `DimProduct` | Dimension | Product catalogue linked to aisle and department |
| `DimDate` | Dimension | Calendar date attributes for time-series analysis |
| `DimDepartment` | Dimension | Store department hierarchy |
| `DimAisle` | Dimension | Aisle-level product grouping |
| `DimRating` | Dimension | Product rating classifications |

---

## ⚙️ ETL Pipeline (SSIS)

ETL workflows were built using **SQL Server Integration Services (SSIS)** in SSDT, covering:

- **Extract** — Ingestion from flat files (`.csv`, `.txt`) across multiple sources
- **Transform** — Data type standardisation, null handling, surrogate key generation, and lookup transformations
- **Load** — Staged loading into dimension and fact tables with referential integrity enforcement

---

## 📊 OLAP Cube (SSAS)

An **SSAS multidimensional cube** was built on top of the data warehouse, enabling high performance analytical queries. The cube supports the following OLAP operations demonstrated via Microsoft Excel:

| Operation | Description |
|-----------|-------------|
| **Roll Up** | Aggregating from product level → aisle → department |
| **Drill Down** | Decomposing department totals down to individual product performance |
| **Slice** | Filtering the cube by a single dimension value (e.g., specific department) |
| **Dice** | Multi-dimensional filtering across two or more dimension values |
| **Pivot** | Rotating axes to reframe data perspective |

---

## 📈 Power BI Reports

Four interactive reports were developed in Power BI, connected to the SSAS cube:

| Report | Description |
|--------|-------------|
| **Matrix Visual Report** | Tabular cross-dimensional view of order metrics by product hierarchy |
| **Slicers with Cascading Filters** | Interactive slicers with parent-child filter dependencies across dimensions |
| **Drill Down Report** | Hierarchical visual allowing in-chart navigation from department → aisle → product |
| **Drill Through Report** | Page-level drill-through enabling contextual deep-dives on selected data points |

---

## 🛠️ Technology Stack

| Category | Tools |
|----------|-------|
| **Database** | SQL Server |
| **ETL** | SQL Server Integration Services (SSIS) |
| **OLAP** | SQL Server Analysis Services (SSAS) |
| **Development** | SQL Server Data Tools (SSDT) |
| **Analysis** | Microsoft Excel (PivotTable connected to SSAS) |
| **Reporting** | Power BI Desktop |

---

## 🚀 Getting Started

### Prerequisites
- SQL Server 2019+ with SSAS and SSIS components installed
- SQL Server Data Tools (SSDT) for Visual Studio
- Power BI Desktop
- Microsoft Excel with Analysis Services add-in

### Setup Steps
1. Restore the SQL Server database from the provided `.bak` file
2. Open the SSIS project in SSDT and update connection strings to your environment
3. Execute ETL packages in dependency order: dimensions first, then fact table
4. Deploy the SSAS project and process the cube
5. Open the Power BI `.pbix` file and refresh the data source connection

---

### Folder Structure
DWBI-Instacart-DataWarehouse-and-BI-Project

├── SSIS_ETL
│   ├── Extract_To_Staging.dtsx
│   ├── Load_DW.dtsx
│   ├── Update_Accumulating_Fact.dtsx
│   └── Screenshots
│
├── SSAS_Cube
│   ├── Cube_Instacart_DW.cube
│   ├── DSV_Instacart_DW.dsv
│   ├── DS_Instacart_DW.ds
│   ├── DimCustomer.dim
│   ├── DimProduct.dim
│   ├── DimDate.dim
│   ├── DimDepartment.dim
│   ├── DimAisle.dim
│   └── Instacart_SSAS.dwproj
│
├── Excel_OLAP
│   └── colab Demonstration.xlsx
│
├── PowerBI
│   └── PowerBi Report.pbix
│
├── Documentation
│   ├── Assignment_1_Report.pdf
│   └── Assignment_2_Report.pdf
│
├── Screenshots
│   ├── DW_Schema.png
│   ├── ETL_Process.png
│   ├── Cube_Design.png
│   ├── Excel_Rollup.png
│   ├── Excel_DrillDown.png
│   ├── Excel_Slice.png
│   ├── Excel_Dice.png
│   ├── Excel_Pivot.png
│   ├── PowerBI_Report1.png
│   ├── PowerBI_Report2.png
│   ├── PowerBI_Report3.png
│   └── PowerBI_Report4.png
│
└── README.md

---

