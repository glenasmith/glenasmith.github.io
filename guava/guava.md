# Guava Workshop


with [Glen Smith](http://blogs.bytecode.com.au/glen)  ( [@glen_a_smith](http://twitter.com/glen_a_smith) )

from [Bytecode](http://www.bytecode.com.au/)



---

## What's on the menu today?

* Guava Mojo
* Files
* Strings
* Boilerplace
* Data Structures
* Caching 
* Functional

---

## How this presentation works

These slides are done in (Reveal.js).

Each section is a "Top Level" slide, then use down arrows to dive deeper

Press the ESC key to go overview

Press S to get to the Speaker notes.


---V

<section data-background="#00ff00">
<h1>You're a sub-slide hero!</h1>
<p>Don't forget you can ESC for overview</p>
</section>

---

## Few words about Why Guava?

* Developed at Google for internal use
* Lots less boilerplace
* Good patterns from smart people
* Absorbs old "Google Collections" lib
* Apache 2 license

---

## Getting started

* Pull in libs
* Make magic happen
* Browse [User Guide](https://code.google.com/p/guava-libraries/wiki/GuavaExplained)
* Bookmark [Javadoc](http://docs.guava-libraries.googlecode.com/git-history/release/javadoc/index.html)

---V

## Pull in the Libs

Add it to your pom.xml, build.gradle or [download it](https://code.google.com/p/guava-libraries/).


```xml
<dependency>
    <groupId>com.google.guava</groupId>
    <artifactId>guava</artifactId>
    <version>15.0</version>
</dependency>
```

---V

## Stopwatch

* More reliable than System.currentTimeMillis()
* Formatted toString()
* Output time in your own units

```java
Stopwatch stopwatch = Stopwatch.createStarted();
doExpensiveOperation();
stopwatch.stop(); // optional

long seconds = stopwatch.elapsed(TimeUnit.SECONDS);

log.info("time: " + stopwatch); // formatted string like "12.3 ms"

stopwatch.reset()
```
