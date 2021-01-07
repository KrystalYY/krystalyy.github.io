https://www.grpc.io/docs/what-is-grpc/introduction/

In gRPC, a client application can directly call a method on a server application on a different machine as if it were a local object.

Client and Server and be written in different languages.

By default, gRPC uses Protocol Buffers for data serialization, which makes payloads faster, smaller and simpler.

gRPC uses HTTP/2 to makes use of binary data rather than just text which makes the communication more compact and more efficient.

## REST VS gRPC

* when creating a web service that expects several client-calls at the same time, and uses a small payload as input and output, REST might be the better choice.
* in all other occasions, gRPC is faster
