# Spacebin Server Configuration Options

* `host (String)`: Host address to serve on.
* `port (Number)`: Port number to serve on.
* `idLength (Number)`: Length of Document IDs to generate.
* `maxDocumentLength (Number)`: Max age of documents.
* [`dbOptions`](#database-options)
  * See the ["Database Options"](#database-options) section for more information.
* [`rateLimits`](#rate-limiting)
  * `requests (Number)`
  * `every (Number)`
  * See the ["Rate Limiting"](#rate-limiting) section for more information.

## Rate Limiting

Spacebin has builtin rate-limiting thanks to [`koa-ratelimit`](https://github.com/koajs/ratelimit).

We use a [`Map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) to store data related to rate limiting. A Redis option may be available in the future.

There are two options related to configuring `koa-ratelimit`:

* `requests (Number)`: The number of requests that can be made before rate-limiting takes effect. 
* `every (Number)`: A millisecond value that controls how often the rate-limiter will be reset.

## Database Options

These are TypeORM configuration options. Usually you will only want to change the ones related to authentication, however due to the current nature of Spacebin's configuration handler you have full access to the TypeORM config through this field.

The structure of this data must follow that of any TypeORM config, defined [here](https://typeorm.io/#/connection-options/).

**NOTE:** Changing the values `synchronize`, and `entities` is highly unrecommended as these options can lead to data-loss or a broken server.
