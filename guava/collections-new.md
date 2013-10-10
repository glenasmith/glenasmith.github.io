# New Collection Types

* MultiSet
* MultiMap
* BiMap
* Table

---V

## Multisets

* A set which counts!
* HashMultiSet, TreeMultiSet
* But a true collection. What does .count() return?

```java
// sample here
```


---V

## MultiMap

* Yes! Finally a Map<K, List<V>>
* Not a true map, since get() returns a non-null collection to add to

```java
// sample here
```

---V

## BiMap

* A Map you can reference by key or value!
* Saves having two makes that you have to sync
* Allows you to view the "inverse" BiMap<V, K> with inverse()
* Ensures that values are unique, making values() a Set
* put() can throw IllegalArgumentException! (forcePut() is your friend)

```java
BiMap<String, String> userIdToEmail = HashBiMap.create();
userIdToEmail.put("glen_smith", "glen@bytecode.com.au");
String userId = userIdToEmail.inverse().get("glen@bytecode.com.au");
```
---V

## Table

* Implements a Table-structure with Row, Column, Value mapping
* Provides ways to iterate entire table, or Maps of certain cols

```java
Table<String, String, String> carsTable = HashBasedTable.create();
carsTable.put("Holden", "Colour", "Blue");
carsTable.put("Holden", "Model", "VY");
carsTable.put("Ford", "Model", "XA");

carsTable.row("Holden"); // returns a Map mapping "Colour" to "Blue", "Model" to "VY"
carsTable.column("Model"); // returns a Map mapping "Holden" to "VY", "Ford" to "XA"
```

---V



