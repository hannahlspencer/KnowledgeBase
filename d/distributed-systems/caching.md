# Caching

Caching takes advantage of the idea that recently requested data is likely to be requested again.

Content Distribution Network (CDN) CDNs are for sites serving a large amount of static media. A request will ask the CDN for a piece of static media which it will serve if it has it locally available. If not, the CDN queries the backend servers, cache it locally, and serve it to the requesting user.

If the system isn’t big enough for its own CDN, we could serve static media off a separate subdomain using a lightweight HTTP server like Nginx for a similar result, and to ease the transition into CDN if it’s ever needed.

#### Cache invalidation

Caching needs maintenance to keep it consistent with the database. If the data is modified in the database, it needs to be invalidated in the cache. If not, the application becomes inconsistent.

Solve this with cache invalidation. Three main schemes of cache invalidation:

* Write-through cache: data is written into the cache and the corresponding database at the same time. This is great for consistency, but has higher latency as every write has to be done twice&#x20;
* Write-around cache: similar to write-through, but cache is bypassed. This reduces the cache being flooded with write operations that won’t be re-read, but a read request for recently written data will have a cache miss, and must be read from slower backend storage&#x20;
* Write-back cache: data is written to cache alone and completion is immediately confirmed to the client. The write to the actual database is then done in specified intervals or under certain conditions. This has low latency and high throughput for write-intensive applications, but risks data loss as if the cache crashes all that data is lost

#### Cache eviction policies

* First In First Out (FIFO) - evicts the first block accessed first without considering how often it has been accessed&#x20;
* Last In First Out (LIFO) - evicts the block accessed most recently without considering how often it has been accessed&#x20;
* Least Recently Used (LRU) - evicts the least recently used items first&#x20;
* Most Recently Used (MRU) - evicts the most recently used items first&#x20;
* Least Frequently Used (LFU) - evicts those items are are used least often&#x20;
* Random Replacement (RR) - randomly selects a candidate to discard
