# Long-Polling, WebSockets, and Server-Sent Events

All three are communication protocols between a client like a web browser and a web server. Sequence of events for a regular HTTP request: The client opens a connection and requests data from the server The server calculates the response The server sends the response back to the client on the opened request

#### Ajax Polling

The client repeatedly polls (or requests) a server for data and waits for the server to respond. If no data is available an empty response is returned.

The client opens a connection and requests data from the server using regular HTTP The requested webpage sends requests to the server at regular intervals (eg. 0.5 seconds) The server calculates the response and sends it back, like regular HTTP traffic The client repeats the above three steps periodically to get updates from the server

The problem with Polling is that the client has to keep asking the server for new data, which means a lot of results are empty so creates HTTP overhead.

#### HTTP Long-Polling

This variation on traditional polling allows the server to push information to a client whenever the data is available.

If the server has no data for the client, instead of sending an empty response the server holds the request and waits until some data becomes available. Once available, the full response is sent to the client. The client then immediately re-requests information so the server will always have an available waiting request to deliver data on a change.

The client makes an initial request using regular HTTP and waits for response The server delays its response until an update is available or there’s a timeout When an update is available, the server sends the full response to the client The client then sends a new long-poll request

Each long-poll request has a timeout so the client has to periodically reconnect after the connection is closed due to timeouts.

#### Websockets

WebSocket provides full duplex communication channels over a TCP connection ie. data can be carried in both directions at the same time. It provides persistent connection between client and server that both parties can use to send data at any time.

The client starts a WebSocket connection through a WebSocket handshake. The WebSocket protocol allows for communication between client and server with lower overheads, allowing real-time data transfer from and to the server.

#### Server-Sent Events (SSEs)

Under SSEs the client has a persistent and long-term connection with the server. The server uses this to send data to the client. If the client wants to send data to the server it would have to use a different technology or protocol.

Client requests data from server using regular HTTP The requested web page opens a connection to the server The server sends the data to the client whenever there’s new information available

SSEs are best for real-time traffic from server to the client, or if the server is generating data in a loop and will be sending multiple events to the client.
