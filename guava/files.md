# Files

* Copying, Renaming
* Simple reading & writing
* Most of this is replace in Java 7

---V

## Reading a file

* Slurping in as a list of String
* Pulling in a byte[]
* Convert lines to Objects

```java
List<String> allLines = Files.readLines(new File("test.txt"), Charsets.UTF_8);

byte[] allFileBytes = Files.toByteArray(new File("image.png"));

List<Account> allAccounts = Files.readLines(new File("accounts.txt"),
    Charsets.UTF_8, new LineProcessor<List<Account>>() {
      @Override public boolean processLine(String string) throws IOException { }

      @Override public List<Account> getResult() { };
});
```

---V

## Writing a File

```java
File outFile = new File("target/writeme.txt");
Files.write("Nothing to see here. Move along.", outFile, Charsets.UTF_8);
Files.append("\nNo, really.", outFile, Charsets.UTF_8);
```
---V

## Move/Rename a file

```java
File from = new File("old.txt");
File to = new File("new.txt");
Files.move(from, to);
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
Files.touch(new File("touching.txt"));
```

---V

## Names and Extensions

* Extracting file names and extension from Strings

```java
String txt = Files.getFileExtension("testing.txt");
String testing = Files.getNameWithoutExtension("testing.txt");
```
---V

## Misc Directory Stuff

* Create all parent dirs to a file (but not the file)

```java
Files.createParentDirs(new File("/create/path/to/file.txt"));
```
