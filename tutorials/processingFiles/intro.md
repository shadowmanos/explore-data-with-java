---
title: File Processing
description: Create, read, update and delete disk files and folders with Kotlin REPL
date: 2019-11-01 00:00:00
layout: default
---

Practical tutorials on programmatically and interactively managing and modifying files and folders with the Kotlin REPL. Unbeknownst to outsiders, this is a big part of data science work! You may want to perform:
 
 1. an operation on the file itself like copy, move, rename or delete.
 2. an operation on the file's contents like append or delete lines of text.
 3. invoke a data processing method on each line of a text or chunk of a binary file.
 4. read or write files in JSON, YAML, XML, HTML, CSV etc formats employing temporary data structures.
  
The functionality of standard Kotlin and Java libraries is enough for most of these operations, and the API is easy to use from a REPL. [Jackson](https://github.com/FasterXML/jackson) will be used to parse files in specific formats like JSON.

### Tutorials

1. [Operations on files](fileOperations.md) 
