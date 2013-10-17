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

```java
String faveCols = "Glen=Orange;Kylie=Aqua;Isaac=Blue;Zoe=Yellow";
Map<String,String> userToColour = Splitter.on(";")
	.withKeyValueSeparator("=")
	.split(faveCols);
assertEquals("Orange", userToColour.get("Glen"));
```

---V

## Joiner

* Where there is split() there must be join()
* has skipNulls() and useForNull("?")

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

* Join a map to a String withKeyValueSeparator()

```java
Map<String,Integer> mapToJoin = ImmutableMap.of("one", 1, "two", 2, "three", 3);
        
String joined = Joiner.on(",").withKeyValueSeparator("=").join(mapToJoin);
assertEquals("one=1,two=2,three=3", joined);
```


---V

## Char Matching

* Much nicer than Regexp!
* Lots of constants CharMatcher.WHITESPACE, JAVA_DIGIT, ASCII, ANY
* Lots of factory goodness: CharMatch.is('x'), isNot(), oneOf(), inRange()

```java
assertTrue(CharMatcher.DIGIT.matches('0'));
assertTrue(CharMatcher.DIGIT.matchesAllOf("123456789"));
assertTrue(CharMatcher.WHITESPACE.or(CharMatcher.DIGIT).
                or(CharMatcher.JAVA_LOWER_CASE).matchesAllOf("abc 123"));
assertEquals("123-def", CharMatcher.anyOf("cba").collapseFrom("123abcdef", '-'));
assertEquals("123def", CharMatcher.anyOf("cba").removeFrom("123abcdef"));
assertEquals("abc", CharMatcher.anyOf("cba").retainFrom("123abcdef"));
```

---V

## Applying CharMatcher

* matchesAllOf(), matchesAnyOf(), matchesNoneOf()
* indexIn(), lastIndexIn(), countIn()
* removeFrom(), retainFrom()
* trimFrom(), trimLeadingFrom(), trimTrailingFrom()
* collapseFrom(), trimAndCollapseFrom()
* replaceFrom()

```java
int whatAmI = CharMatcher.WHITESPACE.or(CharMatcher.anyOf(",.!")).lastIndexOf(myString);
```


