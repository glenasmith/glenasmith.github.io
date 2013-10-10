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
LoadingCache<String,Person> personDetailsCache = 
    CacheBuilder.newBuilder
          .expireAfterWrite(10, TimeUnit.MINUTES)
          .build(new CacheLoader<String,Person>() {
              public Person load(String userId) {
                return ldapService.findByUser(userId);
              }
          }
              
```

---V

## More advanced options

* Explicit invalidation: Cache.invalidate(key); Cache.invalidateAll()
* Options to store weak keys/values
* If cache was started with recordStats(), can call Cache.stats() to get stats back
* Configure your own .removalListener() to cleanup on removal
* Provides asMap() option which returns ConcurrentMap 

