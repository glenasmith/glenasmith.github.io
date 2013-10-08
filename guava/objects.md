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

---V

## Working with Preconditions

* Checks parameter values
* Static imports make it clean
* Throws IllegalArgumentException
* Note that %s is a placeholder *not* the same as String.format!

```java
if (itemsSold < 1) {
   throw new IllegalArgumentException("Must sell at least one item, invalid sale count: ", itemsSold);
}
```

Versus...


```java
checkArgument(itemsSold > 0, "Must sell at least one item, invalid sale count: %s", itemsSold); 
```


---V

## More useful preconditions

* checkNotNull() // throws a NPE back with your message
* checkState()  // checking my own state is valid regardless of params


 

