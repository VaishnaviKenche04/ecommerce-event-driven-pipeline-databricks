# ecommerce-event-driven-pipeline-databricks
Event-driven ETL pipeline on Databricks with SCD Type 2 dimension tracking
An event-driven ETL pipeline built on Databricks that ingests multi-source e-commerce data (customers, orders, products, inventory, shipping), validates and enriches it, and merges it into target dimension/fact tables using a Slowly Changing Dimension (SCD) Type 2 pattern — triggered automatically on file arrival, with no manual scheduling.
