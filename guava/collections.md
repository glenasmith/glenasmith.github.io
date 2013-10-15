# Collections

* Takes advantage of Generics
* Reduces boilerplate

---V

## Generics working for you

* Infers type from target
* Uses varargs for extra awesomeness

```java
List<String> empty = Lists.newArrayList(); 
List<String> names = Lists.newArrayList("Glen", "Kylie", "Isaac", "Zoe");
Map<String,String> userIdToName = Maps.newHashMap();
```

---V

## Ordering collections

* Using the Ordering class

```java
// sample code here
```

---V


## Immutable Collections

* Really immutable (unlike standard "unmodifiable" Java ones)
* Great for thread safe use
* Safe to return to untrusted clients of your library
* Fast, and memory efficient implementations
* Ordering is preserved

```java
public static final ImmutableSet<String> PEOPLE = ImmutableSet.of("Glen", "Kylie", "Isaac", "Zoe");
```

---V

## Building Immutable Collections

* Fluent interfaces for longer of() construction
* Helpful for more complex collections (Multimaps)

```java
ImmutableMap<Integer, String> postcodes = new ImmutableMap.Builder<Integer,String>()
                .put(2600, "Tony")
                .put(2615, "Glen")
                .build();
assertEquals("Tony", postcodes.get(2600));
```

---V

## Reasoning about Sets

* Offers difference(), symetricDifference(), intersection(), union()

```java
Set<String> first = Sets.newHashSet("a", "b", "c");
Set<String> second = Sets.newHashSet("c", "d", "e");

assertEquals(ImmutableSet.of("a", "b"), Sets.difference(first, second)); 
assertEquals(ImmutableSet.of("a", "b", "d", "e"), Sets.symmetricDifference(first, second)); 
assertEquals(ImmutableSet.of("c"), Sets.intersection(first, second)); 
assertEquals(ImmutableSet.of("a", "b", "c", "d", "e"), Sets.union(first, second)); 
```




