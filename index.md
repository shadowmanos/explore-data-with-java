---
title: Interactive data analysis with Kotlin cookbook
description: Bitesize data analysis snippets using the Kotlin REPL
date: 2019-04-14 00:00:00
layout: default
---

### Introduction

This is a cookbook with examples of data analysis using the Kotlin [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop). It's hopefully useful to Java or Kotlin developers who don't want to switch to another language + ecosystem to do some data analysis task interactively, that would then be difficult to "translate" to a JVM language. [Kotlin](https://kotlinlang.org/) has a REPL that can be used within an [Intellij](https://www.jetbrains.com/idea/) project and auto-import from libraries declared in the project's pom.xml or build.gradle. To follow examples in here it'd be great to have basic knowledge of Kotlin, mostly around [collections](https://kotlinlang.org/docs/reference/collections.html), [ranges](https://kotlinlang.org/docs/reference/ranges.html), [lambdas](https://kotlinlang.org/docs/reference/lambdas.html#lambda-expressions-and-anonymous-functions) and [Destructuring Declarations](https://kotlinlang.org/docs/reference/multi-declarations.html).

### Replaying the examples in Intellij

To replay, and most importantly expand on, the examples you read in this cookbook, you'll need jdk 1.8 or later and Intellij, the community edition of which can be downloaded for free from [here](https://www.jetbrains.com/idea/download).

Create a new "Project from version control", select git and put this URL

`https://github.com/shadowmanos/kotlin-repl-data-cookbook.git`

After it's open and Intellij and gradle have done their thing, go the project view on the left, highlight the _main_ module in _src_ folder (that's actually necessary) and choose from menu _Tools_ -> _Kotlin_ -> _Kotlin REPL_. Then start typing code from the examples in this cookbook and (only) if you autocomplete the necessary classes will be auto imported while typing.

Tips:

1. Enter doesn't execute the current line in the REPL, you'll need Cmd+Enter or Ctrl+Enter for that. 
2. You may define a shortcut to bring up the REPL window.

### Contents

1. [CoreNLP](recipes/corenlp/intro.md)
