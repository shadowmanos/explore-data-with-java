---
title: Exploratory data analysis and processing with Kotlin REPL
description: Simple and short tutorials to analyze and transform data interactively using the Kotlin REPL
date: 2019-08-01 00:00:00
layout: default
---

### Introduction

Say you see some text or binary data on some disk files, a website or a database. You want to run some exploratory analysis for some initial conclusions, not sure what algorithm or technique is appropriate. Or you are rather certain about the process, but it's a one off data migration to a different format and save in a different location. So not interested in building and deploying a full-fledged backend application but rather do it interactively from a command line interface, some trial and error inevitable. Some people use Python for example for such tasks. But if you are mainly or exclusively building applications with Java or Kotlin and you are well familiar with Intellij and libraries in the JVM ecosystem, you don't want to have to switch or even learn from scratch a completely different language + ecosystem for the occasional data migration task. Thankfully, Intellij comes with a decent [Kotlin](https://kotlinlang.org/) [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) that you can use. This blog's aims to provide easy and straightforward tutorials for a variety of such tasks that using the Kotlin REPL. There is no particular order just jump to the page relevant to your current problem. Each tutorial is based on the library or API that seems (to me at least) easier to use from the a command line. You won't have to define multiple new classes spread in multiple files as you do with applications. Just type a short line of code, see the results and think of your next step. Intellij also has a Java REPL that only works with a JDK version 9 or later. But it's not anywhere near as practical as the Kotlin one, which additionally works with a version 8 JDK that most developers still use at work. Also, Kotlin allows simpler and more concise solutions for many of these tasks compared to Java. Prior basic knowledge of Kotlin would be useful, mostly around [collections](https://kotlinlang.org/docs/reference/collections.html), [ranges](https://kotlinlang.org/docs/reference/ranges.html), [lambdas](https://kotlinlang.org/docs/reference/lambdas.html#lambda-expressions-and-anonymous-functions) and [Destructuring Declarations](https://kotlinlang.org/docs/reference/multi-declarations.html). But an exclusively Java developer familiar with Java 8 streams should be able to immediately understand most of these tutorials and learn a bit of Kotlin in the process!

### Replaying the examples in Intellij

To follow these tutorials on your machine you'll need JDK 1.8 or later and [Jetbrains Intellij](https://www.jetbrains.com/idea/), the community edition of which can be downloaded for free from [here](https://www.jetbrains.com/idea/download). Kotlin's REPL can be used within a project in Intellij and it will auto-import classes from dependencies declared in the project's pom.xml or build.gradle. So if you git clone and import in Intelij the project in this github repository, it'd be easier to follow all tutorials on your machine:

1. In Intellij go to _File_ -> _New_ -> _Project from version control_ -> _Git_, and put this URL:

`https://github.com/shadowmanos/explore-data-with-kotlin-repl.git`

2. After it's open and Intellij and gradle have done their thing, go the project view on the left, highlight the _main_ module in _src_ folder and choose from menu _Tools_ -> _Kotlin_ -> _Kotlin REPL_. Then start typing code from the examples in this cookbook and (only) if you autocomplete the necessary classes will be auto imported while typing. Alternatively, copy and paste the list of import statements from the end of each page.
 
You may continue reading blog posts online or open the markdown files in the _tutorials_ folder and Intellij will render them. You can navigate to a referenced markdown file same way you navigate to code e.g. Ctrl + Click

Tips:

1. You may define a keyboard shortcut to bring up the REPL window. 
2. Use Enter to type multi-line code in the REPL and Cmd+Enter or Ctrl+Enter to execute.
3. To see all lines For multiline output move the cursor over a visible line (hover) and scroll upwards.
4. A result number and type will appear if you don't assign the result to a variable e.g. 
   ```kotlin
   "a"+"b"
   ```
   ```text
   res1: kotlin.String = ab
   ``` 
5. You can avoid the above and get somewhat cleaner output by using print e.g.
   ```kotlin
   print("a"+"b")
   ```
   ```text
   ab
   ```
6. Assign a result to recall later by name e.g.
   ```kotlin
   val text = "a" + "b"
   ```
   or you may recall a result by the auto-assigned name like `res1`
7. `println` in iterations doesn't seem to work so we'll use something like `print("text\n")`

### Contents

1. [Natural Language Processing](tutorials/naturalLanguage/intro.md)
