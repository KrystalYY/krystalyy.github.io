# Socket

## unix socket
it's a way to talk to other computers using standard Unix file descriptors.

A file descriptor is just an integer associated with an open file and it can be a network connection, a text file, a terminal, or something else (stdin - 0, stdout - 1, stderr - 2).

Linux systems limit the number of file descriptors that any one process may open to 1024 per process (can adjust). 

A Unix Socket is used in a client-server application framework to establish connection adnd exchange data, it encapsulates the underliying protocols (TCP/UDP)

A socket is a unique pair of (client host, client port, server host, server port, protocol).

#### workflow
A server would create a special socket that binds with its host and port (no client host and port) and listens for connections. (`bind()` -> `listen()`). When a request comes, it accpets it (`accept()`), and creates a new socket (with all 5 identifiers) to represent this connection. The listening socket is not affected and continues to listen to new request.(https://man7.org/linux/man-pages/man2/accept.2.html)

#### socket types (2 mostly used):
* stream socket: use TCP, guaranteed and ordered delivery
* datagram socket: use UDP, not guaranteed

## python socket library

#### socket families
Various socket families are supported, can specify when creating the socket object, the specified family decides the socket address format being used.
1. `AF_UNIX`, socket bound to a file system node, address format: string or byte-like object
2. `AF_INET`, address format: (`host`[internet domain|IPv4 address|'' binds to all interfaces|'\<broadcast\>'], `port`)

#### functions
https://docs.python.org/3.7/library/socket.html#socket.socket.accept
* `socket.socket(family=AF_INET, type=SOCK_STREAM, proto=0, fileno=None)`
* `socket.bind(address)`
* `socket.listen([backlog])`
* `socket.accept()` 
* `socket.recv(bufsize[, flags])`
* `socket.close()`
