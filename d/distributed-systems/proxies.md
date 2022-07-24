# Proxies

A proxy server is an intermediate server between the client and backend server, which acts as a middleman between the two. They are generally used to filter, log, or transform requests (eg. by adding/removing headers, compressing, or encrypting/decrypting). Proxy servers also have a cache that can serve a lot of requests. If multiple clients access a single resource, the proxy server can cache it and serve it to all the clients without going to the remote server.

#### Reasons for using a forward proxy

* _To avoid state or institutional browsing restrictions_ - Some organizations use firewalls to give their users access to a limited version of the Internet. A forward proxy can get around these restrictions, as they let the user connect to the proxy rather than directly to the sites they are visiting.
* _To block access to certain content_ - Conversely, proxies can also be set up to block a group of users from accessing certain sites. For example, a school network might be configured to connect to the web through a proxy which enables content filtering rules.
* _To protect their identity online_ - Users may desire increased anonymity online. If a user uses a forward proxy to connect to a website to post a comment, the IP address used to post the comments will be harder to trace back to them as only the IP address of the proxy server will be visible.

#### Proxy server types

_Open proxy_ - accessible by any internet user. There are two main open proxy types:

* Anonymous proxy: reveals its identity as a server but does not disclose the initial IP address
* Transparent proxy : identifies itself with its first IP address. The benefit of this is its ability to cache websites.

_Reverse proxy_ - A reverse proxy is a server that sits in front of one or more web servers, intercepting requests from clients. This is different from a forward proxy, where the proxy sits in front of the clients. With a reverse proxy, when clients send requests to the origin server of a website, those requests are intercepted at the network edge by the reverse proxy server. The reverse proxy server will then send requests to and receive responses from the origin server.

A simplified explanation is that a forward proxy sits in front of a client and ensures that no origin server ever communicates directly with that specific client. On the other hand, a reverse proxy sits in front of an origin server and ensures that no client ever communicates directly with that origin server.

#### Benefits of a reverse proxy

* _Load balancing_ - On a distributed system a reverse proxy can provide a load balancing solution which will distribute the incoming traffic evenly among the different servers to prevent any single server from becoming overloaded. In the event that a server fails completely, other servers can step up to handle the traffic.
* _Protection from attacks_ - With a reverse proxy in place, a web site or service never needs to reveal the IP address of their origin server(s). This makes it much harder for attackers to leverage a targeted attack against them, such as a DDoS attack. Instead the attackers will only be able to target the reverse proxy, such as Cloudflare’s CDN, which will have tighter security and more resources to fend off a cyber attack.
* _Caching_ - A reverse proxy can also cache content, resulting in faster performance. For example, if a user in Paris visits a reverse-proxied website with web servers in Los Angeles, the user might actually connect to a local reverse proxy server in Paris, which will then have to communicate with an origin server in L.A. The proxy server can then cache (or temporarily save) the response data. Subsequent Parisian users who browse the site will then get the locally cached version from the Parisian reverse proxy server, resulting in much faster performance.
* _SSL encryption_ - Encrypting and decrypting SSL (or TLS) communications for each client can be computationally expensive for an origin server. A reverse proxy can be configured to decrypt all incoming requests and encrypt all outgoing responses, freeing up valuable resources on the origin server.
