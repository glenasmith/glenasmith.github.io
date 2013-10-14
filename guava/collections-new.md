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
Multiset<Integer> postcodes = HashMultiset.create();
postcodes.add(2615);
postcodes.add(2615);
postcodes.add(2600);
assertEquals(3, postcodes.size());
assertEquals(2, postcodes.count(2615));

```


---V

## MultiMap

* Yes! Finally a Map of Key to List of Values
* Not a true map, since get() returns a non-null collection to add to

```java
Multimap<Integer, String> postcodeToUserId = ArrayListMultimap.create();
postcodeToUserId.put(2615, "glensmith");
postcodeToUserId.put(2615, "kyliesmith");
postcodeToUserId.put(2600, "tonyabbott");
Collection<String> belcoUsers = postcodeToUserId.get(2615); // Glen & Kylie
assertEquals(3, postcodeToUserId.size());
postcodeToUserId.removeAll(2615);
assertEquals(1, postcodeToUserId.size());
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
assertEquals("glen_smith", userIdToEmail.inverse().get("glen@bytecode.com.au"));
```
---V

## Table

* Implements a Table-structure with Row, Column, Value mapping (think Spreadsheet)
* Provides ways to iterate entire table, or Maps of certain cols

```java
Table<String, String, String> carsTable = HashBasedTable.create();
carsTable.put("Holden", "Colour", "Blue");
carsTable.put("Holden", "Model", "VY");
carsTable.put("Ford", "Model", "XA");

Map<String,String> holdenDetails = carsTable.row("Holden"); 
assertEquals("Blue", holdenDetails.get("Colour"));
assertEquals("VY", holdenDetails.get("Model"));

Map<String,String> modelDetails = carsTable.column("Model"); 
assertEquals("VY", modelDetails.get("Holden"));
assertEquals("XA", modelDetails.get("Ford"));
```





