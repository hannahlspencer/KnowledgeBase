# System Design

### Step by step approach

1. **Clarify requirements**

Ask about exact scope including:

* Types of data being used and stored
* Idea of scale for reads and writes
* Exact parts of the application that need to be written

2. **System interface definition**

Define the APIs expected from the system, eg. for a Twitter clone there would be postTweet, generateTimeline.

3. **Back of envelope estimation**

What's the scale of the system? How many users would we have? How much storage would we need? What's the network bandwidth?

4. **Define data model**

What are the domain objects and what parameters would they have? For example a User might have username, ID, address etc.

5. **High-level design**

Draw several boxes representing core components, eg. databases, application server, load balancer.

6. **Detailed design**

Dig deeper into each component eg. how to partition data in the databases, would we need a cache and where to put it.

7. **Identify and resolve bottlenecks**

Is there any single point of failure? How would we monitor the application? Do we have enough replicas of data?

### Resources

#### Articles

* [31 system design interview questions (and sample answers)](https://igotanoffer.com/blogs/tech/system-design-interviews)
