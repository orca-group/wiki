# Spacebin Server Configuration Options

## `server`

* `server.host`: Host address to serve on (default: `"127.0.0.1"`).
* `server.port`: Port number to serve on (default: `9000`).
* `server.use_csp`: Whether or not to send a CSP header along with responses (default: `true`).
* `server.compress_level`: The level of compression to apply to responses. For more information see [the Fiber documentation](https://git.io/JUX9S) (default: `1`).
* `server.prefork`: Whether or not the server should run across multiple processes (default: `false`).

### `server.ratelimits`

* `server.ratelimits.requests`: How many requests to allow per `duration` (default: `80`).
* `server.ratelimits.duration`: How many milliseconds until the rate limit is lifted. (default: `60_000`). 

## `database`

* `database.dialect`: The kind of database to connect to. Possible values are `mysql`, `sqlite`, or `postgresql` (default: `"sqlite"`).
* `database.connection_uri`: The location of the database to connect to (default: `"./spacebin.db"`). **NOTE:** When connecting to MySQL databases you must pass the `parseTime=True` option.  
  
## `documents`

* `documents.id_length`: The length of identifiers to generate for documents (default: `8`).
* `documents.max_document_length`: The maximum amount of bytes a document can be (default: `400_000`).
* `documents.max_age`: The amount of days documents are stored in the database before they're auto-deleted (default: `90`). 

## Example configuration

An example configuration is already provided in the Spacebin Spirit repository. It is repeated here for convenience.

```toml
[server]
host = "127.0.0.1"
port = 9000
use_csp = true
compress_level = 1
prefork = false

[server.ratelimits]
requests = 80
duration = 60_000 # in ms

[database]
dialect = "sqlite"
connection_uri = "spacebin.db"

[documents]
id_length = 12
max_document_length = 400_000
max_age = 90 # in days
```
