---
title: Works on my machine
description: Necessary steps before trying the tutorials on your machine
date: 2019-08-01 00:00:00
layout: default
---

To try the code in these tutorials on your machine you'll need JDK 1.8 or later, available as per the operating system you use, and [Jetbrains Intellij](https://www.jetbrains.com/idea/), the community edition of which can be downloaded for free from [here](https://www.jetbrains.com/idea/download). Kotlin's REPL can be used after you open a Java or Kotlin project in Intellij, and it will auto-import classes from dependencies declared in the project's pom.xml or build.gradle. So if you git clone and import in Intellij the (based on gradle) project of this github repository, it'd be easier to follow all tutorials on your machine:

1. In Intellij go to _File_ -> _New_ -> _Project from version control_ -> _Git_, and put this URL:

`https://github.com/shadowmanos/explore-data-with-kotlin-repl.git`

2. After it's open, gradle has finished downloading half the internet and Intellij has done its thing, go the project view on the left pane, expand and highlight the _main_ module inside the _src_ folder and choose from menu _Tools_ -> _Kotlin_ -> _Kotlin REPL_. On the pane that opens, start typing code from the examples in this cookbook and (only) if you autocomplete the necessary classes will be auto imported while typing. Alternatively, there is a list of import statements at the first paragraph of each tutorial and if you copy and paste it into the REPL you can then copy and paste each line of code without bothering with autocomplete. For these import statements to work, you still need to highlight the main module in the left pane.
 
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
7. `println` in iterations doesn't seem to add a new line, so we'll use something like `print("text\n")`
