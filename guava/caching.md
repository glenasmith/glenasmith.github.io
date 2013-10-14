# Caching

* Formerly MapMaker, Now CacheBuilder
* Purely RAM-based
* Great for lazy-loading Maps with eviction
* No new threads required

---V

## Simple Expiring Caches

* Lazy loading
* Timeouts in human units or constrain on size .maximumSize(entries);
* Support expireAfterAccess() or expireAfterWrite()
* NB: will perform cache maintenance on read/writes ONLY

```java
final AtomicInteger counter = new AtomicInteger();
        
LoadingCache<String, Account> accountDetailsCache
        = CacheBuilder.newBuilder()
        .expireAfterWrite(1, TimeUnit.SECONDS)
        .build(new CacheLoader<String, Account>() {
            public Account load(String userId) {
                return new Account(userId, Integer.toString(counter.incrementAndGet()), 
                        userId + "@sample.com");
            }
        });

Account glen = accountDetailsCache.get("glen");
assertEquals("1", glen.getPassword());
glen = accountDetailsCache.get("glen");
assertEquals("1", glen.getPassword());

Thread.sleep(1100);

glen = accountDetailsCache.get("glen");
assertEquals("2", glen.getPassword());
glen = accountDetailsCache.get("glen");
assertEquals("2", glen.getPassword());
              
```

---V

## More advanced options

* Explicit invalidation: Cache.invalidate(key); Cache.invalidateAll()
* Options to store weak keys/values
* If cache was started with recordStats(), can call Cache.stats() to get stats back
* Configure your own .removalListener() to cleanup on removal
* Provides asMap() option which returns ConcurrentMap 

