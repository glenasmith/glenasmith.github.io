# Error Handling

* Reduce boilerplace
* Design by Contract
* Working with Exceptions

---V


## Working with Preconditions

* Checks parameter values
* Static imports make it clean
* Throws IllegalArgumentException
* Note that %s is a placeholder *not* the same as String.format!

```java
if (itemsSold < 1) {
   throw new IllegalArgumentException("Must sell at least one item, invalid sale count: " + itemsSold);
}
```

Versus...


```java
checkArgument(itemsSold > 0, 
   "Must sell at least one item, invalid sale count: %s", itemsSold); 
```


---V

## checkNotNull()

* Throws a NPE with your message

```java
public String upper(@NotNull String lowerString) {
	checkNotNull(lowerString, "We only support not null values");
    return lowerString.toUpperCase();
} 
```

---V

## checkState()

* Checking my own state is valid regardless of params

```java
checkState(init == true, "Please call init() before using object");
```

---V

## Working with Exceptions

* Provides convenient ways to access Exception chain
* Handy ways of rethrowing and tunnelling exceptions

---V

## Exception Utils

```java
Throwable getRootCause(Throwable)
List<Throwable> getCausalChain(Throwable)
String getStackTraceAsString(Throwable)
```

---V

## Propagating Exceptions

```java
Throwables.propagateIfInstanceOf(t, IOException.class);
throw Throwables.propagate(t); // wraps in a runtime exception if required 
```
 
---V

## Optionals

* Mirrors what's coming in Java 8
* Nullsafe returns for explicit resolve

```java
private Optional<String> toLower(String incoming) {
	if (incoming != null) {
	    return Optional.of(incoming.toLowerCase());
	} else {
	    return Optional.absent();
	}     
}
```


```java
Optional<String> lower = toLower("HI");
assertTrue(lower.isPresent());
assertEquals("hi", lower.get());

lower = toLower(null);
assertFalse(lower.isPresent());        
String defaultMe = lower.or("bye");
assertEquals("bye", defaultMe);  
```
