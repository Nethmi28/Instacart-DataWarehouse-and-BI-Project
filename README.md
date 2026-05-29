# Data Warehousing and Business Intelligence Project

## Overview

This project demonstrates the complete implementation of a Business Intelligence solution using the Instacart Online Grocery Basket Dataset.

The project includes:

- Data Warehouse Design
- ETL Development using SSIS
- SSAS Cube Development
- OLAP Operations using Excel
- Interactive Power BI Reports

## Technologies

- SQL Server
- SSIS
- SSAS
- SSDT
- Microsoft Excel
- Power BI

### Dataset 
https://www.kaggle.com/datasets/yasserh/instacart-online-grocery-basket-analysis-dataset?

### Data Sources

1. Instacart Online Grocery Basket Dataset
   Source: Kaggle
   link -https://www.kaggle.com/datasets/yasserh/instacart-online-grocery-basket-analysis-dataset?

2. Customer data generated using Mockaroo

Files used:
- Aisles.csv
- Departments.txt
- Products.csv
- Ratings.txt

## Data Warehouse Design

Snowflake schema consisting of:

### Fact Table
- FactOrder

### Dimensions
- DimCustomer
- DimProduct
- DimDate
- DimDepartment
- DimAisle
- DimRating

## OLAP Operations Demonstrated

- Roll Up
- Drill Down
- Slice
- Dice
- Pivot

## Power BI Reports

### Report 1
Matrix Visual Report

### Report 2
Slicers with Cascading Filters

### Report 3
Drill Down Report

### Report 4
Drill Through Report
