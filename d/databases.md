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

### Resources

#### Articles

* [When to use Cassandra](https://medium.com/geekculture/system-design-solutions-when-to-use-cassandra-and-when-not-to-496ba51ef07a)
