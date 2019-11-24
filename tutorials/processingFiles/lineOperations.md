---
title: Manger file contents line by line
description: Add, remove, modify and process lines of a text or binary file
date: 2019-11-01 00:00:00
layout: default
---

### First line

Following on [File operations](fileOperations.md) where we managed files as a unit, we now want to manage the contents of a text or binary file with some form of tabular data.

For text files this could be a comma separated list of data items in each line (a CSV format). E.g. the actor name, character name, series abbreviation and number of seasons of first 2 Star Trek Series:

```csv
Patrick Stewart,Jean-Luc Pickard,NG,7
Willian Shatner,James Kirk,TOS,3
```

A binary file could have a known count of known size numbers in each line without delimiters. E.g. The start year 1966, end year 1967 and number of episodes 29 of first season of Star Trek the Original Series in binary with sizes 16bit, 16bit, 8bit:

```text
0000011110101110000001111011100100011101
```
