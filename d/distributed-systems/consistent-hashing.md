# Consistent Hashing

**Problem**: we have a distributed caching system, give n servers we have the hash function key % n.&#x20;

This has the issues of:&#x20;

* It is not horizontally scalable - whenever a new cache host is added all existing mappings break
* It is not load balanced - especially for non-uniformly distributed data, for which some caches will be overused and some empty

Consistent hashing allows us to distribute data across a cluster that will minimise reorganisation when nodes are added or removed so that only k/n keys will need to be remapped where k is the total number of keys and n is the number of servers.

How it works:

Given a list of cache servers, hash them to integers in the range To map a key to a server Hash it to a single integer Move clockwise on a ring until finding the first cache it encounters That cache is the one that contains the key

For load balancing we add virtual replicas for caches. Instead of mapping each cache to a single point in the ring, we map it to multiple. So each cache is associated with multiple points on the ring.
