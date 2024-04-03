# Reliable, Scalable, Maintainable Applications

These applications should be fault resilient, ie. continues to work correctly even when things go wrong.&#x20;

Fault is a deviation from expectation; failure is a whole system stopping.

It's common to trigger faults to find them, eg. Netflix's Chaos Monkey. From those findings error handling can be improve. Tolerance of faults is better than attempting total prevention.

#### How to help reliability in the face of human fallibility?

* Design - well-designed abstractions & APIs make it harder to do the 'wrong' thing
* Decouple common mistakes and failure opportunities ie. use a sandbox environment to explore and experiment safely
* Test all levels: unit to integration to manual
* Ensure rolling back is easy & deployments are done with small changes
* Monitoring!

#### Scalability

* What is load? Requests per second, active users, database read/writes.
* Consider fan-out load eg. for Twitter, if a use has 30 million foloowers the load of putting their tweet into every follower's feed is way more than for someone with 30 followers.

For online systems response time is most important.

* Response time - what the client sees, including network and queuing delays
* Latency - duration that a request is waiting to be handled

Median is a good metric for typical wait times aka. p50, or the 50th percentile.

High percentiles of response times (p99) are known as tail latencies, but those customers are often very important and make a lot of requests. These become more important for backend services that are called multiple times for a single user request. One slow call can disrupt the rest.

#### Approaches to coping with load

* Scaling up/vertical scaling - moving to a more powerful machine
* Scaling out/horizontal scaling - distributing loads across multiple machines

Distributing stateful systems is more more complex than distributing stateless ones.

#### Maintainability

Trying to minimise pain during maintenance and updates with design principles:

* Operability - make it easy for operations teams to keep the system running smoothly
* Simplicity - make it easy for new engineers to understand the system by removing complexity
* Evolvability - make it easy for engineers to make changes in the future aka. extensibility

Use abstraction to remove accidental complexity.

#### Distributed Data

Why distribute data? For scalability, availability, and latency.

* Shared memory architecture - all components can be treated as a single machine (vertical scaling)
* Shared-nothing architecture - each machine running the database is a node, which uses its CPUs and RAM independently (horizontal scaling)

