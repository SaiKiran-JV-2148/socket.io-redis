
# socket.io-redis

## How to use

```js
var io = require('socket.io')(3000);
io.adapter(require('socket.io-redis')({ host: 'localhost', port: 6379 ));
```

By running socket.io with the `socket.io-redis` adapter you can run
multiple socket.io instances in different processes or servers that can
all broadcast and emit events to and from each other.

If you need to emit events to socket.io instances from a non-socket.io
process, you should use
[socket.io-emit](http:///github.com/learnboost/socket.io-emit).

## API

### adapter(opts)

The following options are allowed:

- `key`: the name of the key to pub/sub events on as prefix (`socket.io`)
- `host`: host to connect to redis on (`localhost`)
- `port`: port to connect to redis on (`6379`)
- `pubClient`: optional, the redis client to publish events on
- `subClient`: optional, the redis client to subscribe to events on

If you decide to supply `pubClient` and `subClient`, make sure you use
[node_redis](https://github.com/mranney/node_redis) as a client or one
with an equivalent API.

If you supply clients, make sure you initialized them with 
the `return_buffers` option set to `true`.

## License

MIT
