---
title: Exploratory data analysis and processing with Kotlin REPL
description: Simple and short tutorials to analyze and transform data interactively using the Kotlin REPL
date: 2019-08-01 00:00:00
layout: default
---

### What's this all about

You have some text or binary data on some disk files, a website or a database. You want to do some exploratory analysis, draw some initial conclusions, not sure what algorithm or technique will work best. Or you are actually certain about the process, but it's a one off data migration to a different format and data store. In any case, you don't want to build and deploy a full-fledged backend application. Rather, do it simply and interactively from a command line interface. Some people use scripting languages like Python for example for such tasks. On the other hand, if you are mainly or exclusively building applications with Java or Kotlin and you are well familiar with Intellij and libraries in the JVM ecosystem, you don't want to have to switch or even learn from scratch a completely different language + ecosystem for the occasional data migration task. Thankfully, Intellij comes with a decent [Kotlin](https://kotlinlang.org/) [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) that you can use. This blog's aims to provide easy and straightforward tutorials for a variety of such tasks that employ the Kotlin REPL. There is no particular order, go straight to the page relevant to your current problem. Each tutorial employs a library or API that seems (to me at least) easier to use from the command line. You won't have to define multiple classes, methods, factories, services, configuration files, repositories etc as you do with applications. Just type a short line of Kotlin code, maybe use a lambda you defined before, see the results and decide on the next step. Intellij also has a Java REPL that only works with a JDK version 9 or later. Unfortunately, it's not as practical as the Kotlin one, which additionally works with a version 8 JDK that most developers still use at work. Also, Kotlin allows simpler and more concise solutions for many of these tasks compared to Java. Prior basic knowledge of Kotlin would be very useful but not entirely necessary. A decent Java 8 developer, familiar with streams and lambdas, should be able to understand the Kotlin code in these tutorials. You may want to have a quick read about [collections](https://kotlinlang.org/docs/reference/collections.html), [ranges](https://kotlinlang.org/docs/reference/ranges.html), [lambdas](https://kotlinlang.org/docs/reference/lambdas.html#lambda-expressions-and-anonymous-functions) and [Destructuring Declarations](https://kotlinlang.org/docs/reference/multi-declarations.html).

### Contents

1. [Natural Language Processing](tutorials/naturalLanguage/intro.md)
2. [File reading and writing](tutorials/processingFiles/intro.md)
