# Databases

#### SQL vs. NoSQL

SQL is suited to:&#x20;

* data with set schemes, especially ones that need multi-row transactions
* data that must be consistent eg. accounting/financial

SQL databases are usually vertically scalable - can increase the load on a single server.



NoSQL is suited to:

* companies with rapid growth
* No clear schema definitions/evolving schemas and data structures
* Large quantities of data that need to be analysed
* Large/regularly changing datasets

NoSQL are horizontally scalable - increased traffic is handled by adding more servers



#### CAP Theorem

CAP theorem states that distributed databases can one have one of three properties:

1. Consistency (all reads receive the same most recent write or an error)
2. Availability (all reads receive a response, but it may not be the most recent)
3. Partition tolerance (the system continues to work despite network failures)

NoSQL can not provide consistency and high availability together.

#### Indexes

When database performance is no longer satisfactory one of the first things to do is indexing. The goal of creating an index is to make it faster to search through the table. Indexes can be created using one or more columns to provide the basis for random lookups and efficient access of ordered records.

Indexes are a data structure that acts a table of contents that points us to the location of the actual data. When an index is created on a column, we store that column and a pointer to the whole row in the index.

Indexes are a necessity for data sets that are many terabytes in size with small payloads, especially if the data is spread over several physical devices. However an index can slow down data insertion and update. When adding rows or making updates to a table with an active index, both the data and the index has to be written or updated. For this reason unnecessary indexes should be avoided, especially in databases that are often written to and rarely read from.

### Resources

#### Articles

* [When to use Cassandra](https://medium.com/geekculture/system-design-solutions-when-to-use-cassandra-and-when-not-to-496ba51ef07a)
