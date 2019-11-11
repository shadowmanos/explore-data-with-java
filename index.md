---
title: Exploratory data analysis and processing with Kotlin REPL
description: Simple and short tutorials to analyze and transform data interactively using the Kotlin REPL
date: 2019-08-01 00:00:00
layout: default
---

### What's this all about

You have some text or binary data on some disk files, a website or a database. You want to do some exploratory analysis, draw some initial conclusions, not sure what algorithm or technique will work best. Or you are actually certain about the process, but it's a one off data migration to a different format and data store. In any case, you don't want to build and deploy a full-fledged backend application. Rather do it simply and interactively from a command line interface. Some people use scripting languages like Python for example for such tasks. But if you are mainly or exclusively building applications with Java or Kotlin and you are well familiar with Intellij and libraries in the JVM ecosystem, you don't want to have to switch or even learn from scratch a completely different language + ecosystem for the occasional data migration task. Thankfully, Intellij comes with a decent [Kotlin](https://kotlinlang.org/) [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) that you can use. This blog's aims to provide easy and straightforward tutorials for a variety of such tasks that employ the Kotlin REPL. There is no particular order, go straight to the page relevant to your current problem. Each tutorial employs a library or API that seems (to me at least) easier to use from the command line. You won't have to define multiple classes, methods, factories, services, configuration files, repositories etc as you do with applications. Just type a short line of Kotlin code, maybe use a lambda you defined before, see the results and decide on the next step. Intellij also has a Java REPL that only works with a JDK version 9 or later. But it's not anywhere near as practical as the Kotlin one, which additionally works with a version 8 JDK that most developers still use at work. Also, Kotlin allows simpler and more concise solutions for many of these tasks compared to Java. Prior basic knowledge of Kotlin would be very useful but not entirely necessary. A decent Java 8 developer, familiar with streams and lambdas, should be able to understand the Kotlin code in these tutorials. You may want to have a quick read about [collections](https://kotlinlang.org/docs/reference/collections.html), [ranges](https://kotlinlang.org/docs/reference/ranges.html), [lambdas](https://kotlinlang.org/docs/reference/lambdas.html#lambda-expressions-and-anonymous-functions) and [Destructuring Declarations](https://kotlinlang.org/docs/reference/multi-declarations.html).

### Works on my machine

To try the code in these tutorials on your machine you'll need JDK 1.8 or later, available as per the operating system you use, and [Jetbrains Intellij](https://www.jetbrains.com/idea/), the community edition of which can be downloaded for free from [here](https://www.jetbrains.com/idea/download). Kotlin's REPL can be used after you open a Java or Kotlin project in Intellij, and it will auto-import classes from dependencies declared in the project's pom.xml or build.gradle. So if you git clone and import in Intelij the (based on gradle) project of this github repository, it'd be easier to follow all tutorials on your machine:

1. In Intellij go to _File_ -> _New_ -> _Project from version control_ -> _Git_, and put this URL:

`https://github.com/shadowmanos/explore-data-with-kotlin-repl.git`

2. After it's open, gradle has finished downloading half the internet and Intellij has done its thing, go the project view on the left pane, expand and highlight the _main_ module inside the _src_ folder and choose from menu _Tools_ -> _Kotlin_ -> _Kotlin REPL_. On the pane that opens, start typing code from the examples in this cookbook and (only) if you autocomplete the necessary classes will be auto imported while typing. Alternatively, there is a list of import statements at the end of each tutorial that you can conveniently copy and paste into the REPL and then you can copy and paste each line of code without bothering with autocomplete.
 
You may continue reading blog posts online on github or open the markdown files in the _tutorials_ folder and Intellij will render them with its Markdown plugin. You can navigate to links by clicking if your are viewing in preview mode or Ctrl + Click in edit mode.

Tips:

1. You may define a keyboard shortcut to bring up the REPL window. 
2. Hit Enter to type multi-line code in the REPL and Cmd+Enter or Ctrl+Enter to execute.
3. To see all lines For multiline output move the cursor over a visible line (hover) and scroll upwards.
4. A result number and type will appear if you don't assign the result to a variable e.g. 
   ```kotlin
   "a"+"b"
   ```
   ```text
   res1: kotlin.String = ab
   ``` 
5. You can avoid the above and get a somewhat cleaner output by using print e.g.
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
7. `println` in iterations doesn't seem to work, so we'll use something like `print("text\n")`

### Contents

1. [Natural Language Processing](tutorials/naturalLanguage/intro.md)
