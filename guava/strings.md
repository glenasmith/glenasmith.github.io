# Strings

* Blanks and Nullsafety
* Padding
* Splitting, Joining
* CharMatcher

---V

## Nulls and Blanks

* Lots of nullsafe options for argument passing
* You can safely use them with null or non-null values

```java
Strings.nullToEmpty(null); // returns ""
Strings.nullToEmpty("valid"); // returns "valid"
Strings.emptyToNull("");    // returns null
Strings.emptyToNull("valid"); // returns valid
Strings.isNullOrEmpty(yourString); // returns ?

```

---V

## Padding Strings

* padStart(), padEnd(), repeat()
* commonPrefix(), commonSuffix()


```java

Strings.repeat("win", 3); // winwinwin
Strings.commonPrefix("winning", "wins"); // win
Strings.commonSuffix("bi-winning", "so winning"); // winning
```

---V

## Splitter

* Split strings on delimereter
* Can handle empty and blank strings

```java
Iterable<String> split = Splitter.on(',')
       .trimResults()
       .omitEmptyStrings()
       .split("Glen,Kylie,,  Isaac  , Zoe,");
```

---V

## Splitting to Lists

* If you're returning stuff

```java
List<String> nameList = Splitter.on(',')
       .trimResults()
       .omitEmptyStrings()
       .splitToList("Glen,Kylie,,   ,  Isaac  , Zoe,");
```


---V


## Splitting with CharMatcher & Regepx

* You aren't limited to just delimeters


---V

## Splitting to Maps

* Turning a String into a Map using key/value delims
* 

```java

String faveCols = "Glen=Orange;Kylie=Aqua;Isaac=Blue;Zoe=Yellow";
Map<String,String> userToColour = Splitter.on(";")
	.withKeyValueSeparator("=")
	.split(userToColour);
assertEquals("Orange", userToColour.get("Glen"));
```

---V

## Joiner

* Where there is split() there must be join()

```java
String joined = Joiner.on(",")
	.skipNulls()
	.join("Glen", "Kylie", null, "Isaac", "Zoe");
assertEquals("Glen,Kylie,Isaac,Zoe", joined);
```

---V

## Joining with Custom Null

* Provide your own null substitute

```java
String joined = Joiner.on(",")
	.useForNull("???")
	.join("Glen", "Kylie", null, "Isaac", "Zoe");
assertEquals("Glen,Kylie,???,Isaac,Zoe", joined);
```

---V

## Joining to Maps

* withKeyValueSeparator()

```java
// example here
```


---V

## Char Matching

* Lots of constants CharMatcher.WHITESPACE, JAVA_DIGIT, ASCII, ANY
* Lots of factory goodness: CharMatch.is('x'), isNot(), oneOf(), inRange()

```java
String creditCar = CharMatcher.DIGIT.or(ChartMatcher.is("-").retainFrom(rawCardStr);
```

---V

## Applying CharMatcher

* matchesAllOf(), matchesAnyOf(), matchesNoneOf()
* indexIn(), lastIndexIn(), countIn()
* removeFrom(), retainFrom()
* trimFrom(), trimLeadingFrom(), trimTrailingFrom()
* collapseFrom(), trimAndCollapseFrom()
* replaceFrom()

