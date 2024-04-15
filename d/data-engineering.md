# Data Engineering

### Core concepts

#### Operational and analytical data

* Operational - usually transactional data generated and stored by applications, often in a relational/non-relational database
* Analytical - data that has been optimised for analysis, usually stored in a data warehouse

Need to integrate operational and analytical data sources and/or extract operational data, transform it for analysis, and load it into an analytical store.

#### Streaming data

Perpetual sources of data that generate data values in real-time eg. IoT, social media feeds

#### Data pipelines

Used to orchestrate transfer and transformation activities, that can be triggered by events or a schedule.

#### Data lakes

A storage repository that holds a large amount of data in raw formats. They are optimised for scaling to massive volumes and can be from multiple sources, structured, semi-structured, and unstructured.

#### Data warehouses

This is a centralised repository of integrated data from multiple sources. The data is organised into a schema optimised for analytical queries.

#### Apache Spark

This is a parallel processing framework that uses in-memory processing and distributed file storage.
