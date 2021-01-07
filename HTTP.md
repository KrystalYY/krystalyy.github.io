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
