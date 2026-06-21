# ecommerce-event-driven-pipeline-databricks
Event-driven ETL pipeline on Databricks with SCD Type 2 dimension tracking
An event-driven ETL pipeline built on Databricks that ingests multi-source e-commerce data (customers, orders, products, inventory, shipping), validates and enriches it, and merges it into target dimension/fact tables using a Slowly Changing Dimension (SCD) Type 2 pattern — triggered automatically on file arrival, with no manual scheduling.

docs/screenshots/Architecture.png
The pipeline is structured as a multi-stage Databricks Job with both parallel and sequential stages:

Parallel ingestion — customers_load, inventory_load, orders_load, products_load, shipping_load run concurrently, reading newly arrived files and performing initial data quality checks (null checks, invalid amount checks, valid/invalid record splitting).
Validation — data_validation consolidates and validates records across all sources.
Enrichment — data_enrichment joins and enriches the validated data (e.g. computing profit margin, estimated CLV, seasonal/time-of-day attributes).
Final merge — 08_final_merge_operation merges enriched data into target tables in Unity Catalog using SCD Type 2 logic, and writes a run summary to a processing_log table.


