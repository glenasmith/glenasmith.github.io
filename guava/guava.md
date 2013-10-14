# Guava Workshop


with [Glen Smith](http://blogs.bytecode.com.au/glen)  ( [@glen_a_smith](http://twitter.com/glen_a_smith) )

from [Bytecode](http://www.bytecode.com.au/)



---

## What's on the menu today?

* Guava Mojo
* Files
* Strings
* Boilerplate
* Data Structures
* Caching 
* Functional

---

## Workshop plan

* Introduce concepts
* Give sample code
* Solve a coding challenge
* Explore this presentation yourself

---

> Nothing is taught until something is learned.

---

You can get to these slides at http://glenasmith.github.com/guava/

You can get the matching source project at https://github.com/glenasmith/guava-examples

---

## How this presentation works

These slides are done in [Reveal.js](http://lab.hakim.se/reveal-js/#/).

Each Guava section is a "top level" slide, down arrow to dive deeper

Press the ESC key to go overview

---V

<section data-background="#00ff00">
<h1>You're a sub-slide hero!</h1>
<p>Don't forget you can ESC for overview</p>
</section>

---

## Few words about Why Guava?

* Developed at Google for internal use
* Reduces boilerplate
* Good patterns from smart people
* Absorbs old "Google Collections" lib
* Apache 2 license
* You will use it every day life - it's like riding a Unicorn

---V

## Aside: Guava and Null

* This is a library to teach you about [null safety](https://code.google.com/p/guava-libraries/wiki/UsingAndAvoidingNullExplained)
* Fields that are Nullable are marked [@Nullable](https://code.google.com/p/google-guice/wiki/UseNullable)
* Interesting to explore JSR 305 et al (See [StackOverflow](http://stackoverflow.com/questions/4963300/which-notnull-java-annotation-should-i-use))

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

## Mental Model: Need to Know

* Pluralise things for instant happiness
* Objects, Strings, Lists, Iterators, Maps, Files, Collections2 (!)
* Don't stop loving the JDK: Mix and match


---V

## A first taste: Stopwatch

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
