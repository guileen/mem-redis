mem-redis
=========

High performance cache layer. `mem[key] || redis.get(key)`



NOTE: be careful about state sync
----

process1: 
```js
cache.set('foo', 'bar')
```

process2: 
```js
cache.del('foo')
```

process1: 
```js
cache.get('foo') == 'bar' /* wrong, should be null */
```

process2: 
```js
cache.get('foo') == null
```

