---
title: Interactive data analysis with Kotlin cookbook
description: Bitesize data analysis snippets using the Kotlin REPL
date: 2019-08-01 00:00:00
layout: default
---

### Introduction

This is a cookbook with examples of data analysis using the Kotlin [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop). It's hopefully useful to Java or Kotlin developers who don't want to switch to another language + ecosystem to do some data analysis task interactively and then "translate" to a JVM language. Preference will be given to libraries and APIs that facilitate simple single-line solutions to such tasks. [Kotlin](https://kotlinlang.org/) has a REPL that can be used within an [Intellij](https://www.jetbrains.com/idea/) project and auto-import from libraries declared in the project's pom.xml or build.gradle. To follow examples in here it'd be great to have basic knowledge of Kotlin, mostly around [collections](https://kotlinlang.org/docs/reference/collections.html), [ranges](https://kotlinlang.org/docs/reference/ranges.html), [lambdas](https://kotlinlang.org/docs/reference/lambdas.html#lambda-expressions-and-anonymous-functions) and [Destructuring Declarations](https://kotlinlang.org/docs/reference/multi-declarations.html).

### Replaying the examples in Intellij

To replay, and most importantly expand on, the examples you read in this cookbook, you'll need jdk 1.8 or later and Intellij, the community edition of which can be downloaded for free from [here](https://www.jetbrains.com/idea/download).

Create a new "Project from version control", select git and put this URL

`https://github.com/shadowmanos/kotlin-repl-data-cookbook.git`

After it's open and Intellij and gradle have done their thing, go the project view on the left, highlight the _main_ module in _src_ folder (that's actually necessary) and choose from menu _Tools_ -> _Kotlin_ -> _Kotlin REPL_. Then start typing code from the examples in this cookbook and (only) if you autocomplete the necessary classes will be auto imported while typing. You may continue reading blog posts online or open the markdown files in the recipes folder and Intellij will render them. You can navigate to a referenced markdown file same way you navigate to code e.g. Ctrl + Click

Tips:

1. You may define a shortcut to bring up the REPL window. 
2. Use Enter to type multi-line code and in the REPL and Cmd+Enter or Ctrl+Enter to execute.
3. To see all lines For multiline output move the cursor over a visible line (hover) and scroll upwards.
4. A result number and type will appear if you don't assign the result to a variable e.g. 
   ```kotlin
   "a"+"b"
   ```
   ```text
   res1: kotlin.String = ab
   ``` 
5. You can avoid the above by using print e.g.
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
7. `println` in iterations doesn't seem to work so we'll use something like `print("text\n)`

### Contents

1. [Natural Language Processing](recipes/naturalLanguage/intro.md)
