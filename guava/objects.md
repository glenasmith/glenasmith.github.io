# Objects

* Reduce boilerplace

---V

## equals()

* Null-safe comparisons
* Equivalent to Java7 Objects.equals()

```java
Objects.equals(a, b);
```

---V

## Defining your own toString()

* Equavalent to commons ToStringBuilder()
* Has add() overloads for all primatives
* Fluent APIs common in Guava

```java
// Returns "Customer{name=glen, userId=glen_a_smith}"
   return Objects.toStringHelper(this)
       .add("name", name)
		.add("twitterId", twitterId)
		.omitNullValues()
       .toString();
```

---V


## Find the first non-null

* Return the first non-null
* NOTE: Throws a NPE if both are null!

```java
   String one = null;
   String two = "two";
   String firstNonNull = Objects.firstNonNull(one, two); // two
```

