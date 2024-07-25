Earlier web page was all about: HTML(format to represent content), HTTP(protocol to transfer this content), www(first browser ehre client can see this content), server(where this doc can exist)

1. HTTP(0.9) was all about GET request
2. HTTP(1.0): header in request, content-type in header, status code for broswer to use whether cache to be served
3. HTTP(1.1): Resources embedded in a HTML no need to call a new request, Pipeline added for async request sent an not to wait for prevs resulting in low latency
  Chunked responses were also supported.
  Additional cache control mechanisms were introduced.
  Content negotiation, including language, encoding, and type, was introduced. A client and a server could now agree on which content to exchange.
  Thanks to the Host header, the ability to host different domains from the same IP address allowed server collocation.(HOST is server address)
4. HTTP(2.0): binary protocol rather than a text protocol. multiplexed protocol(parallel request for same connection)
5. HTTP(3.0) runs on UDP instead of TCP saving latency
HTTP/1.1 and HTTP/2.0 are different versions of the HTTP protocol, each designed to improve upon its predecessor in terms of performance, efficiency, and features. Here’s a comparison between HTTP/1.1 and HTTP/2.0:

### HTTP/1.1:

1. **Request/Response Multiplexing**:
   - **HTTP/1.1**: In HTTP/1.1, multiple requests and responses cannot be processed simultaneously over a single TCP connection. This limitation leads to a practice called "head-of-line blocking," where a slow or stalled request can delay others behind it.

2. **Header Compression**:
   - **HTTP/1.1**: Headers are sent with each request and response in plaintext, which can lead to inefficiencies, especially for requests with large headers or cookies.

3. **Resource Bundling**:
   - **HTTP/1.1**: To minimize the number of requests, developers often bundle resources (like CSS, JavaScript, and images) into fewer files. However, this can lead to issues with caching and unnecessary downloads when only part of a bundle changes.

4. **Performance Optimization**:
   - **HTTP/1.1**: Techniques like domain sharding (using multiple domains to circumvent browser connection limits), image sprites (combining multiple images into one to reduce requests), and inlining (embedding small images or CSS directly into HTML) are used to improve performance.

### HTTP/2.0:

1. **Request/Response Multiplexing**:
   - **HTTP/2.0**: Allows multiple requests and responses to be multiplexed over a single TCP connection. This feature eliminates the head-of-line blocking problem and enables more efficient use of network resources.

2. **Header Compression**:
   - **HTTP/2.0**: Headers are compressed using HPACK, a more efficient compression algorithm, which reduces overhead and improves latency.

3. **Binary Protocol**:
   - **HTTP/2.0**: Messages are encoded in binary format instead of plaintext, making parsing more efficient and reducing errors.

4. **Server Push**:
   - **HTTP/2.0**: Allows servers to proactively push resources to the client's cache before they are explicitly requested. This can reduce the number of round-trips needed to render a page, improving performance.

5. **Stream Prioritization**:
   - **HTTP/2.0**: Requests can be assigned priority levels, allowing more important resources to be transmitted and processed more quickly, optimizing page rendering.

### Summary:

- **Performance**: HTTP/2.0 generally offers better performance due to multiplexing, header compression, and other optimizations, reducing latency and improving throughput.
  
- **Compatibility**: Both HTTP/1.1 and HTTP/2.0 are widely supported by browsers and servers. HTTP/2.0 is designed to be backward-compatible with HTTP/1.1, allowing gradual adoption and fallback mechanisms.

- **Adoption**: HTTP/2.0 adoption has been increasing steadily, especially for sites that require improved performance and user experience.

In conclusion, HTTP/2.0 represents a significant improvement over HTTP/1.1 in terms of performance and efficiency, mainly due to multiplexing, header compression, and other advanced features designed to handle modern web applications and improve user experience.
