---
title: NLP Kotlin cookbook
description: Natural Language Processing with Kotlin REPL
date: 2019-04-14 00:00:00
layout: default
---

Practical examples on analysis of plain English text i.e. [Natural Language Processing](https://en.wikipedia.org/wiki/Natural_language_processing). We'll use [Stanford CoreNLP](https://stanfordnlp.github.io/CoreNLP/) and where possible its [Simple API](https://stanfordnlp.github.io/CoreNLP/simple.html) that is more appropriate for a REPL. Language models will be lazy loaded whenever you first use an algorithm that requires this model. 

All text samples used for testing are Star Trek quotes (English not Klingon) sourced from either [Wikipedia](https://en.wikipedia.org/wiki/Star_Trek) or [Memory Alpha](http://memory-alpha.wikia.com/wiki/Portal:Main). After an entirely unscientific thought process, I decided such quotes are grammatically correct, adequately diverse and of average complexity.

Won't bore you with grammar or linguistic theory as this is written from a code monkey's rather than a PhD student's perspective. Think Scotty instead of Spock. You may follow links in blog posts to learn more theory if you are so inclined.

*Disclaimer*: No [tribbles](https://en.wikipedia.org/wiki/Tribble) were harmed in the making of this repository.

### Recipes

1. [CorenNLP Intro](corenNLPIntro.md)
