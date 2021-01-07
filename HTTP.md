## protocol

HTTP/1.0 VS HTTP/1.1
* persistent TCP connection (but within one connection, requests are still sent sequentially)
* OPTIONS method. An HTTP client can use this method to determine the abilities of the HTTP server. It's mostly used for Cross Origin Resource Sharing in web applications.
* cache headers (a lot, cannot really remember unless need to use...)

HTTP/1.1 VS HTTP/2.0 (https://www.digitalocean.com/community/tutorials/http-1-1-vs-http-2-what-s-the-difference)
* the persistent TCP connection may cause head-of-line (HOL) blocking issue, when a request at the head of the queue that cannot retrieve its required resource blocks all the requests behind it, since they are sharing the same connection.
* HTTP/2 uses the binary framing layer to encapsulate all messages in binary format, while HTTP/1.1 transfers these in plain-text messages.
* with binary frames, HTTP/2 uses **multiplexing** to solve the HOL issue, this also means that servers and clients can send concurrent requests and responses.
* each connection has multiple streams, each can be set a weight indicating its priority + dependent stream ID number.

## Life Cycle

https://dev.to/dangolant/things-i-brushed-up-on-this-week-the-http-request-lifecycle- 
https://blog.csdn.net/gybshen/article/details/95618695  (浏览器与服务器，TCP与HTTP)
1. Resolve IP address from configured DNS, DNS servers have hierarchy, if not found in the configured DNS, send request to upper layers until found one
2. Establish TCP connection, 3-way handshake
3. Send HTTP request to request for the resource
4. server process the request, found the resource, generate a HTTP response with some status code
5. for HTTP/1.0 break TCP connection after every HTTP request unless Connection: keep-alive; for HTTP/1.1 bu default reuse TCP connection unless Connection: close 
6. parse HTML, download script and other media files, construct CSS tree
