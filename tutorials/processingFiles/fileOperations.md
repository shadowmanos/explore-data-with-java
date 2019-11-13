---
title: File operations
description: Find, copy, move/rename and delete files
date: 2019-11-01 00:00:00
layout: default
---

### Pre-filing

We'll see some simple one line examples on operations on file themselves without modifying contents. We'll just use standard Java and Kotlin classes.
Steps before your start at [Works on my machine](../../worksOnMyMachine.md) and to import stuff do: `import java.io.*`

### List folders and files

First step is always to create a [File](https://docs.oracle.com/javase/8/docs/api/java/io/File.html) that represents a path to a file or folder. To create one pass a `String` with the path. E.g. to make a `File` out of your home folder:

```kotlin
val home = File(System.getProperty("user.home"))
```

The following will list names of all non-hidden files only in your home folder without going into subfolders:

```kotlin
home.walk()
    .maxDepth(1)
    .filter { f -> f.isFile }
    .filter { f -> !f.isHidden }
    .forEach { n -> print("$f.name\n") }
``` 

Experiment with arguments above to get more desirable results.

To recursively search for files by name and type and get the absolutePath, try the following:

```kotlin
home.walk()
    .filter { f -> f.isFile }
    .filter { f -> f.name.startsWith("travels")}
    .filter { f -> f.name.endsWith("txt")}
    .first()
    .absolutePath
    
```

You may list folders sorted by name like this:

```kotlin
home.walk()
    .maxDepth(1)
    .filter { f -> f.isDirectory }
    .sortedBy { f -> f.name }
    .forEach { f -> print("$f.name\n") }
```

Note that the home folder, the root of this traversal, is included.

`home.walk()` will perform depth-first traversal. You can use `home.walkBottomUp()` for breadth-first.

We may want to filter files per the parent folder. For example count Kotlin source files in a multi-project source code folder. We expect them to be in folders like: `src/main/kotlin`.

```kotlin
home.walk()
    .filter { f -> f.isFile }
    .filter { f -> f.name.endsWith("kt")}
    .filter { f -> f.parent.endsWith == "src/main/kotlin"}
    .count()
```
