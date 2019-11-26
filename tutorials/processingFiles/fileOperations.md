---
title: File operations
description: Find, copy, move/rename and delete files
date: 2019-11-01 00:00:00
layout: default
---

### Pre-filing

We'll see some simple one line examples on operations on files themselves without modifying contents. We'll just use standard Java and Kotlin classes.
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
    .forEach { f -> print("${f.name}\n") }
``` 

[home.walk()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io/java.io.-file/walk.html) will perform depth-first traversal. You can use [home.walkBottomUp()](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.io/java.io.-file/walk-bottom-up.html) for breadth-first.

To recursively search for files by name and type and get the absolutePath, try the following:

```kotlin
home.walk()
    .filter { f -> f.isFile }
    .filter { f -> f.nameWithoutExtension == "someText"}
    .filter { f -> f.extension =="txt"}
    .first()
    .absolutePath
    
```

Or you could filter by `f.name == "someText.txt""` for same result.

Note that with `first()` you can get a new `File` representing a folder, and use it as a basis for future searches:

```kotlin
val docs = home.walk()
    .filter { f -> f.isDirectory }
    .filter { f -> f.name == "Documents"}
    .first()
```

You may list folders sorted by name like this:

```kotlin
home.walk()
    .maxDepth(1)
    .filter { f -> f.isDirectory }
    .sortedBy { f -> f.name }
    .forEach { f -> print("${f.name}\n") }
```

Note that the home folder, the root of this traversal, is included.

We may want to filter files per the parent folder. For example count Kotlin source files in a multi-project source code folder. We expect them to be in folders like: `src/main/kotlin`.

```kotlin
home.walk()
    .filter { f -> f.isFile }
    .filter { f -> f.extension == "kt"}
    .filter { f -> f.parent.endsWith("src/main/kotlin")}
    .count()
```

### Size matters

To get the size of a file:

```kotlin
someFile.length()
```

The above is not useful for folders. To get the size of all files in a folder we need to iterate over them:

```kotlin
home.walk()
    .maxDepth(1)
    .filter { f -> f.isFile }
    .map { f -> f.length() }
    .sum()
```

From any file, you can get usage and size information for the whole disk:

```kotlin
home.freeSpace
home.usableSpace
home.totalSpace
```

Expect `usableSpace` to be less than `freeSpace`

### Modify files

To create a new empty folder:

```kotlin
val someFolder = docs.resolve("someFolder")
someFolder.mkdir()
```

To create a new empty file:

```kotlin
val someText = someFolder.resolve("someText.txt")
someText.createNewFile()
```

you can chain two `resolve` calls, but you have to create a folder before creating a file within it.

We can rename/move a file by:

```kotlin
val movedFile = docs.resolve("someFileMovedToDocs.txt")
someText.renameTo(movedFile)
```

This method take a `File` argument and since the file is under a different folder, it was moved as well as renamed. So it's similar to Unix [mv](https://en.wikipedia.org/wiki/Mv) command. If you now type `someText` to inspect the variable, you'll see it still refers to original path `Documents/someFolder/someText.txt` that no longer exists. Consequently, if you try to rename `someText` again it will fail and return `kotlin.Boolean = false`.

If we wanted to copy instead, keeping the original file:

```kotlin
val copiedFile = someText.copyTo(docs.resolve("someFolder/copyOfSomeText.txt"))
```

which, unlike previous methods, returns a `File` instead of boolean.

If you regret copying the file, to get rid of it:

```kotlin
copiedFile.delete()
```
