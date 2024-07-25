HTTP polling, HTTP long polling, HTTP streaming, and WebSocket are all techniques used for real-time communication between a client (typically a web browser) and a server. Here's a brief overview of each:

1. **HTTP Polling**:
   - **Description**: In HTTP polling, the client repeatedly makes HTTP requests to the server at regular intervals (e.g., every few seconds).
   - **Operation**: The client sends a request to the server, which responds immediately with the current state (or an indication that there's no new data). The client then waits for the next interval to make another request.
   - **Pros and Cons**: Simple to implement, works with standard HTTP servers. However, it can lead to unnecessary requests if there are no updates, which can waste resources and increase latency.

2. **HTTP Long Polling**:
   - **Description**: HTTP long polling is a variation of polling where the server delays its response to the client until new data is available or a timeout occurs.
   - **Operation**: The client sends a request to the server, and the server holds the request open until it has new information to send back to the client. Once the server sends a response, the client immediately sends another request to keep the connection open.
   - **Pros and Cons**: Reduces the number of requests compared to regular polling, but still involves frequent short-lived connections which can be resource-intensive on both server and client.

3. **HTTP Streaming**:
   - **Description**: HTTP streaming involves the server sending continuous data to the client over a single HTTP connection that remains open for a prolonged period.
   - **Operation**: The server sends chunks of data to the client as they become available, without closing the connection after each chunk. The client can begin processing the data as soon as it receives the first chunk, enabling real-time updates.
   - **Pros and Cons**: Provides real-time updates with lower latency compared to polling methods. However, it requires support for chunked encoding on the server side and can be complex to implement.

4. **WebSocket**:
   - **Description**: WebSocket is a protocol that provides full-duplex communication channels over a single TCP connection.
   - **Operation**: Once the WebSocket connection is established, both the client and server can send data to each other at any time, without the overhead of HTTP headers with each message.
   - **Pros and Cons**: Efficient and ideal for real-time applications such as chat applications, online gaming, and financial trading platforms. It reduces latency and overhead compared to HTTP-based techniques. However, it requires both the client and server to support the WebSocket protocol.

**Key Differences**:
- **Polling and Long Polling** involve repeated requests from the client, with Long Polling allowing the server to delay responses until new data is available.
- **HTTP Streaming** sends continuous data over a single connection, suitable for applications needing frequent updates but not real-time duplex communication.
- **WebSocket** provides full-duplex communication over a single TCP connection, making it highly efficient for real-time applications.

Choosing the right technique depends on the specific requirements of your application, such as latency sensitivity, scalability, and client-server interaction patterns.
  Duplex/directional:

Uni-directional: HTTP poll, long poll, streaming.
Bi-direcitonal: WebSockets, plugin networking
In order of increasing latency (approximate):

  - WebSockets
  - Plugin networking
  - HTTP streaming
  - HTTP long-poll
  - HTTP polling
  - CORS (cross-origin support):

WebSockets: yes
Plugin networking: Flash via policy request (not sure about others)
HTTP * (some recent support)
Native binary data (typed arrays, blobs):

WebSockets: yes
Plugin networking: not with Flash (requires URL encoding across ExternalInterface)
HTTP *: recent proposal to enable binary type support
Bandwidth in decreasing efficiency:

Plugin networking: Flash sockets are raw except for initial policy request
WebSockets: connection setup handshake and a few bytes per frame
HTTP streaming (re-use of server connection)
HTTP long-poll: connection for every message
HTTP poll: connection for every message + no data messages
