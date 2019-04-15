---
title: Data analysis cookbook with Kotlin
description: Bitesize data analysis examples using the Kotlin REPL
date: 2019-04-14 00:00:00
layout: default
---

### Introduction

This is a cookbook with examples of data analysis using the Kotlin [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop). It's hopefully useful to Java or Kotlin developers who don't want to switch to another language + ecosystem to do some interactive data analysis task, that would then be difficult to "translate" to a JVM language. [Kotlin](https://kotlinlang.org/) has a REPL that can be used within [Intellij](https://www.jetbrains.com/idea/) with the same libraries used for a Java or Kotlin project and can auto import from dependencies defined in pom.xml or build.gradle files of this project. You only need basic knowledge of Kotlin to follow this.

### Replaying the examples in Intellij

To replay, and most importantly expand on, the examples you read in this cookbook, you'll need Intellij, the community edition of which can be download for free from [here](https://www.jetbrains.com/idea/download).

Then create a new "Project from version control", select git and put this URL

`https://github.com/shadowmanos/kotlin-repl-data-cookbook.git`

You'll need jdk 1.8 or later. After it's open and Intellij and gradle have done their thing, go the project view on the left, highlight the _main_ module in _src_ folder and choose from menu _Tools_ -> _Kotlin_ -> _Kotlin REPL_. Then start typing code from the examples in this cookbook and if you autocomplete the necessary classes will be auto imported while typing. Tip: You may define a shortcut to bring up the REPL window.


### Contents

1. [CoreNLP](recipes/corenlp/intro.md)
