# Leader-based replication

One replica is the leader so the first write always goes to that node. Then this leader sends the data change to its followers. A client can read from any replica.

Should replication be synchronous? ie. should the leader wait until confirmation from every follower before reporting success?

* Pro: every follower is guaranteed to have an up-to-date copy of the data
* Con: if a follower doesn't respond the write won't be processed and the leader will have to block every write until it is

In practice, often only one follower is synchronous. If all were asynchronous then a write can't be guaranteed as durable.

#### New Nodes

When setting up a new follower you could lock the database while copying it over, but that means no availability during that time. The answer: take a snapshot of the database, copy that to the follower, connect to the leader and then request all subsequent changes from the logged time of the snapshot.

#### Handling outages

A follower can catch up from outages with its log, much like when adding a new node. If the leader has an outage one of the followers gets auto-assigned as the new leader, ie. failover. Failover can be manual or automatic.

Cons of failover:

* If replication is asynchronous the new leader might not be up to date. It could discard unreplicated writes, but that undermines durability
* Two nodes may start to act as leader simultaneously which would cause write conflicts
* No right amount of time to wait to declare the leader dead. If the timeout is too long then recovery is more difficult, if too short then failover is unnecessary
