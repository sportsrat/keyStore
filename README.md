# keyStore - A redis like key value store

### Overview
Tried to implement a redis like key value store in C++. This server utilizes a single event loop with `epoll` to manage multiple clients at once.  It supports a subset of Redis commands and follows the Redis Serialization Protocol (RESP) for client-server communication. It supports Key Value stores, List Stores and Hash Stores.

---

### Features
- RESP Parsing
- Non-Blocking I/O : Uses `epoll` for handling multiple connections on a single thread.
- Persists data to disk
- Graceful shutdown with signal handling

---

### Commands that are implemented

#### Basic Commands

- `PING` - Checks whether the Redis server is running
  - Output: `PONG`
- `ECHO` - Returns the message provided by the user
  - Output: `Whatever the user types`
- `FLUSHALL` - Deletes all keys from all Redis databases
  - Output: `OK`

#### KV Commands

- `SET` - Sets a key-value pair
- `GET` - Retrieves the value associated with a key
- `KEYS` - Finds keys matching a given pattern
- `TYPE` - Returns the data type of a key
- `DEL` - Deletes one or more keys
- `EXISTS` - Checks whether a key exists
- `RENAME` - Renames an existing key
- `EXPIRE` - Sets a time-to-live (TTL) for a key
- `TTL` - Returns the remaining TTL of a key

#### List Commands

- `LLEN` - Returns the length of a list
- `LRANGE` - Retrieves a range of elements from a list
- `LPUSH` - Adds one or more elements to the left/head of a list
- `RPUSH` - Adds one or more elements to the right/tail of a list
- `LPOP` - Removes and returns the first element of a list
- `RPOP` - Removes and returns the last element of a list
- `LREM` - Removes elements matching a specified value
- `LINDEX` - Retrieves an element at a specific index
- `LSET` - Updates the element at a specific index

> **Note:** `LGET` is not a standard Redis command. `LRANGE` or `LINDEX` should be used to retrieve list elements.

#### Hash Commands

- `HSET` - Sets one or more field-value pairs in a hash
- `HGET` - Retrieves the value of a specific hash field
- `HDEL` - Deletes one or more fields from a hash
- `HEXISTS` - Checks whether a field exists in a hash
- `HGETALL` - Returns all fields and values in a hash
- `HKEYS` - Returns all fields in a hash
- `HVALS` - Returns all values in a hash
- `HLEN` - Returns the number of fields in a hash---

### Todo:
- [] Implement more commands
- [] Add connection timeout and buffer limit
