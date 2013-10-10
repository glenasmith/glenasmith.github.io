# Caching

* Formerly MapMaker, Now CacheBuilder
* Purely RAM-based
* Great for lazy-loading Maps with eviction

---V

## Simple Expiring Caches

* Lazy loading
* Timeouts in human units

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

