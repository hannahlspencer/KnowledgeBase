# Distributed Systems

### Key characteristics of distributed systems

#### 1. Scalability

Scalability is the capability of a system to grow and manage increased demand.

* Vertical scales by adding more power (CPU, RAM, storage) to an existing server&#x20;
* Horizontal - adding more servers to the pool of resources

Horizontal is often easier to scale dynamically; Vertical is limited to the capacity of a single server

Cassandra and MongoDB are both good examples of horizontal scaling by adding more machines MySQL is a good example of vertical scaling as it allows an easy way to scale by switching from smaller to bigger machines (though this can often involve downtime)

#### 2. Reliability

Reliability is the probability a system will fail in a given period. A distributed system is reliable if it keeps delivering services even when one or more of its software or hardware components fail. This is achieved through redundancy, which in itself is costly.

#### 3. Availability

Availability is the time a system remains operational in a specific period, taking into account repair time etc. Reliability is availability over time, considering the full range of possible real-world conditions that can occur.

If a system is reliable, it is available, but this does not work the other way around. High reliability contributes to high availability, but you can have an available product with low reliability eg. a store with 99.99% availability could be vulnerable to security incidents that then would cause low availability for repairs.

#### 4. Efficiency

There are two measures of a system’s efficiency:&#x20;

* Response time (or latency) - the delay to obtain the first item&#x20;
* Throughput (bandwidth) - the number of items delivered in a given time

These can translate to the number of messages sent regardless of message size, and the message size itself. This is arguably too simplistic to measure the performance of distributed systems, but it can be difficult to do this precisely so this rough estimate is considered robust enough.

#### 5. Serviceability/Manageability

How easy is the system to operate and maintain? If the time to fix a system increases, its availability decreases. Should consider the ease of diagnosing problems when they occur, and how to detect these as early as possible with logging, monitoring, and alerting.
