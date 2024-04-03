# Replication log methods

#### Statement-based replication

* The leader logs every write and each follower acts as if they got it directly
* Con: if a function like Now() or an incrementing method is used then followers will have different results

#### Write-ahead log shipping

* Every write is appended to a log which builds a copy of everything in the node
* Con: describes data at a very low level so if, eg, the storage format gets changed then it can't be run as it's coupled with the storage engine

#### Logical (row-based) log replication

* Sequence of records for the writes at row granularity, so decoupled from the storage logs
* This is better for backwards compatability

#### Trigger-based replication

* Replication at the application layer, which happens when a certain change occurs in the database
* This has greater overheads and can be buggy, but the flexibility is useful
