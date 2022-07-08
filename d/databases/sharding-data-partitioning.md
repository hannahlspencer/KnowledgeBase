# Sharding/Data partitioning

A technique that breaks up a big database into smaller parts across multiple machines to improve performance, availability, manageability, and load balancing. After a certain scale point scaling horizontally is cheaper and easier than scaling vertically.

#### Partitioning methods

* _Horizontal partitioning_&#x20;

Put different rows into different table eg. decide that locations with ZIP codes less than 10000 can go in one table and more than can go in another. However if this value to partition on isn’t chosen carefully the servers can become unbalanced.

* _Vertical partitioning_

Divide data to store tables related to a feature on their own server. EG. instagram - one server for data related to users, one to photos, one to follow lists.

Vertical has low impact on the application, but if it grew a lot then it may be necessary to partition further which would mean completely reshuffling the data

* _Directory based partitioning_

Create a lookup service which knows your current partitioning scheme and abstracts it away from the DB access code. So to find some data we query the directory server that holds the mapping between each tuple key to its DB server. This allows us to add servers and change our partition scheme without impacting the application.

#### Partitioning Criteria

* _Key or hash based partitioning_&#x20;

Apply a hash function to some key attributes of entity that makes a partition number eg. we have 100 DB servers and the ID is numeric that gets incremented by 1 each time a record is inserted. The hash function could be “ID % 100” which will give us the server number we can read/store the record.

This approach should ensure the uniform allocation of data BUT it fixes the total number of DB servers, and adding more servers would create huge overhead. Can fix this with consistent hashing.

* _List partitioning_&#x20;

Each partition is assigned a list of values, so whenever we want to insert a new record we can see which partition contains our key and store it there eg. all users living in Europe would be in one partition whereas the US would be in another

* _Round-robin partitioning_&#x20;

Each value stored gets put into a different partition in a round robin style. Ensures uniform data distribution

* _Composite partitioning_&#x20;

Combine any of the above to devise a new scheme eg. consistent hashing could be a composite of hash and list partitioning where the hash reduces the key space to a size that can be listed

#### Common problems of sharding

* _Joins and denormalisation_&#x20;

Performing joins on a database running on multiple machines is often not possible. These joins will not be performance efficient as data has to be compiled from multiple servers. Can fix this by denormalising the database so queries that previously required joins can be performed from a single table, but this can lead to data inconsistency.

* _Referential integrity_&#x20;

Trying to enforce data integrity constraints such as foreign keys can be very difficult, and applications that require referential integrity on sharded databases often have to enforce it in application code.

* _Rebalancing_&#x20;

If we need to change our sharding scheme (eg. one shard has too much load) we need to create more DB shards or rebalance existing one. This means the partitioning scheme changes and all existing data must be moved. Doing this without downtime is hard. Using a scheme like directory based partitioning makes this easier, but at the cost of increasing system complexity and creating a new single point of failure.
