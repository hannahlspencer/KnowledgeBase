# Load Balancing

Purpose of load balancers:

* &#x20;help spread the traffic across a cluster of servers to improve responsiveness and availability of applications, websites, or databases
* keep track of the status of these resources while distributing requests so if a server is down or has an elevated error rate, traffic is no longer routed to it.

Load balancers generally sit between the client and a set of servers. This prevents one server from being a single point of failure, improving availability and responsiveness. Load balancers can sit in three places:&#x20;

* Between the user and the web server&#x20;
* Between web servers and internal platform later (eg. application layer or cache)&#x20;
* Between internal platform layer and database

Load balancers can be a single point of failure, so should have a second load balancer connected to the original to form a cluster.

#### Benefits of load balancing&#x20;

* Users get a faster, uninterrupted service&#x20;
* Service providers experience less downtime and higher throughput&#x20;
* Decreases wait time for users&#x20;
* Smart load balancers offer benefits like predictive analytics to decrease traffic bottlenecks as they happen&#x20;
* Instead of a single device performing a lot of work, several devices do a bit of work which results in fewer failed or stressed components

#### Load balancing algorithms



_Least connection method_

* &#x20;Directs traffic to the server with the fewest active connections - useful when there are many persistent client connections that are unevenly distributed

_Least response time method_&#x20;

* Directs traffic to the server with the fewest active connections AND lowest average response time

_Least bandwidth method_&#x20;

* Selects the server currently serving the least amount of traffic in megabits per second

_Round Robin method_&#x20;

* Cycles through a list of servers and sends each new request to the next server. Useful when servers are of equal specification and there aren’t many persistent connections

_Weighted round robin_&#x20;

* Designed to better handle servers with different processing capacities. Each server is assigned a weight, and servers with higher weights receive new connections before, and more of them than, those with less weight

_IP Hash_&#x20;

* Hash of the IP address of the client is calculated to redirect the request to a server
