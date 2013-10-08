# Files

* Copying, Renaming
* Simple reading
* Most of this is replace in Java 7

---V

## Reading a file


```java
List<String> allLines = Files.readLines(new File("test.txt"), Charsets.UTF_8);
byte[] allFileBytes = Files.readBytes(new File("image.png"));
```

---V

## Move/Rename a file


```java
File from = new File("old.txt");
File to = new File("new.txt");
Files.copy(from, to);
```

---V

## Copying a file


```java
File from = new File("src.txt");
File to = new File("dest.txt");
Files.copy(from, to);
```

---V

## Touching a file

* Creates an empty file

```java
Files.touch(new File("touch.txt"));
```

---V

## Names and Extensions

```java
String txt = Files.getFileExtension("testing.txt");
String testing = Files.getNameWithoutExtension("testing.txt");
```
---V

## Misc Directory Stuff

* Create parent dirs

```java
createParentDirs(new File("/create/path/to/file.txt"));
```
