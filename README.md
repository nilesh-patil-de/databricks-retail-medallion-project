
# Databricks Retail Medallion Architecture Project

## Overview

This project demonstrates an end-to-end Data Engineering pipeline built using Databricks, PySpark, Delta Lake, GitHub, and Databricks Workflows.

The pipeline follows the Medallion Architecture pattern:

Bronze → Silver → Gold

## Architecture

Online Retail CSV
        ↓
Databricks Volume
        ↓
Bronze Layer
        ↓
Silver Layer
        ↓
Gold Layer
            ├── country_sales
            ├── monthly_revenue
            └── top_products

## Technologies Used

- Databricks
- PySpark
- Delta Lake
- Unity Catalog
- Databricks Workflows
- GitHub
- SQL

## Bronze Layer

### Table

retail_project.bronze.online_retail

### Purpose

- Raw data ingestion
- Delta table creation
- Initial validation

## Silver Layer

### Table

retail_project.silver.online_retail

### Transformations

- Removed duplicates
- Removed invalid records
- Filtered null descriptions
- Filtered invalid prices
- Added transaction_type column

## Gold Layer

### country_sales

Country-wise revenue aggregation.

### monthly_revenue

Monthly revenue trend analysis.

### top_products

Top revenue-generating products excluding postage-related records.

## Workflow Orchestration

Databricks Workflow DAG:

bronze_ingestion
        ↓
silver_transformation
        ↓
 ┌──────┼─────────┐
 ↓      ↓         ↓
country monthly  products
sales   revenue

## Key Results

- 541,909 source records processed
- 534,129 clean Silver records
- Country-level revenue KPIs
- Monthly revenue trend analysis
- Product performance analytics

## Future Enhancements

- Incremental loading
- Auto Loader
- Delta Live Tables
- CI/CD using Databricks Asset Bundles
- Power BI dashboard integration
