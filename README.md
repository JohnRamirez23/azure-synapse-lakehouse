# Azure Synapse Lakehouse Project
## Overview

This project implements an end-to-end analytical data platform in Azure using a Lakehouse architecture. 
The solution ingests transactional data from Azure SQL Database into Azure Data Lake Storage Gen2, applying incremental ingestion, data transformations and governance best practices.

The pipeline is orchestrated using Azure Synapse Analytics and follows the Medallion Architecture (Bronze, Silver and Gold layers) to ensure scalability, data quality and analytics readiness.

## Architecture

The solution is designed following a Lakehouse architecture pattern, separating ingestion, processing and analytics layers to ensure scalability and maintainability.

### High-level components

- **Source**: Azure SQL Database (OLTP system)
- **Orchestration**: Azure Synapse Analytics Pipelines
- **Storage**: Azure Data Lake Storage Gen2
- **Processing**: Synapse Data Flows / Apache Spark
- **Analytics Layer**: Synapse Serverless SQL Pool
- **Secrets Management**: Azure Key Vault

## Data Flow

1. Data is extracted incrementally from Azure SQL Database using a watermark-based strategy.
2. Extracted data is stored in the **Bronze** layer in raw CSV format for traceability and reprocessing.
3. Data is transformed, typed and normalized in the **Silver** layer using columnar Parquet format.
4. Business-ready datasets are published in the **Gold** layer, optimized for analytics and reporting.
5. Data quality validations are applied between layers to ensure consistency and reliability.

## Medallion Architecture

- **Bronze Layer**: Stores raw data as ingested from the source systems, without transformations.
- **Silver Layer**: Contains cleaned, typed and standardized data ready for analytical processing.
- **Gold Layer**: Provides curated, business-ready datasets optimized for consumption by BI tools and analytics workloads.

## Technologies Used

- Azure Synapse Analytics
- Azure Data Lake Storage Gen2
- Azure SQL Database
- Azure Key Vault
- Apache Spark
- GitHub

## Security

- All sensitive information such as connection strings and credentials is managed using **Azure Key Vault**.
- Azure **Managed Identities** are used to authenticate services securely without hardcoded secrets.
- Access permissions follow the **principle of least privilege**.

## Cost Optimization

- Serverless SQL Pools are used to avoid fixed compute costs.
- Resources are configured using minimal SKUs suitable for development environments.
- Columnar storage formats are leveraged to reduce storage footprint and improve query performance.

## How to Run (High-level)

1. Provision the required Azure resources (Synapse Analytics, ADLS Gen2, Azure SQL Database).
2. Configure Linked Services and integrate Azure Key Vault.
3. Deploy and configure Synapse pipelines.
4. Execute the ingestion pipeline and validate data across Bronze, Silver and Gold layers.

## Project Status

This project is under active development and will be continuously enhanced with additional features such as advanced data quality checks, monitoring and automation.
