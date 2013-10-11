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
* Great for threat safe use
* Safe to return to untrusted clients of your library
* Fast, and memory efficient implementations

```java
public static final ImmutableSet<String> PEOPLE = ImmutableSet.of("Glen", "Kylie", "Isaac", "Zoe");
```

---V

## Comparison Chain

* Great for implementing Comparable

```java
// sample code here
```
