#File Input / Output
* To read from a file, you got to have a scanner:
```java
Scanner in = new Scanner(Paths.get("myfile.txt"), "UTF-8");
// now you can use any of the Scanner methods
```
* To write to a file, make a `PrintWriter` object:
```java
PrintWriter out = new PrintWriter("myfile.txt", "UTF-8");
// you can now use print, println, printf
```

----
* `Scanner(Path p, String encoding);`
* `static Path get(String pathname);` -- *Constructs Path from string*
