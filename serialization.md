## Pickle in Python

Used for setialization and de-serialization of python objects, but it is not recommended to use if you want to use data across different programming languages, or different version of python.

## JSON

Language-independant, human readable, fast.

## XML

Poor performance.

##  Protocol Buffers

https://developers.google.com/protocol-buffers/docs/pythontutorial

More efficient for communication and storage, supports RPC (procedure call).

`.proto` file => compile => data access classes, and corresponding accessor functions like `name()` and `set_name()`, as well as methods to serialize/parse the whole structure to/from raw bytes.
