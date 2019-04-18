---
title: Baby steps
description: Simplest NLP tasks
date: 2019-04-18 00:00:00
layout: default
---

### Documents, sentences and words

Let's start by creating a [Document](https://nlp.stanford.edu/nlp/javadoc/javanlp/index.html?edu/stanford/nlp/simple/Document.html) with appropriate sample text for starting our journey.

```kotlin
val text = Document("""Space: the final frontier.
These are the voyages of the starship Enterprise.
Its continuing mission: to explore strange new worlds,
to seek out new life and new civilizations,
to boldly go where no one has gone before!""")
```

The simplest processing we can do here is split the document into [sentences](https://nlp.stanford.edu/nlp/javadoc/javanlp/index.html?edu/stanford/nlp/simple/Sentence.html) and a sentence into words. Note that it splits documents on punctuation like '.' and '!' if followed by a space and it retains the punctuation in the resulting sentences. It doesn't split on ',' or ':'. It splits sentences to words on whitespace and punctuation marks are isncluded as words. With CoreNLP we can usually extract info either a list with the plural form of a method e.g. `sentences()` or get a specific element with the singular form and a 0-based index e.g. `sentence(1)`. Try:

```kotlin
val sentence = text.sentence(1)
```

We'll use the `sentence` variable later.

```kotlin
sentence.word(1)
```
```text
res1: kotlin.String! = are
```

### Lemmas

While speaking we transform words from the basic, root form like _go_ to other appropriate forms like _goes_ or _went_. The basic, root form is called [lemma](https://simple.wikipedia.org/wiki/Lemma_(linguistics)) and it's obvious from this example we can't always just take a substring of a word to find a lemma. We can easily find lemmas with CoreNLP. For example the lemma of _are_, second word of second sentence is _be_:

```kotlin
sentence.lemma(1)
```
```text
res2: kotlin.String! = be
```

### Parts of speech

CoreNLP will do its best to guess whether a word is a verb, noun, adjective etc. That is a **P**art **O**f **S**peech tag and you can learn more about these [here](https://en.wikipedia.org/wiki/Part_of_speech) and see a neat list of potential tags at [Penn tree bank](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html). You loved grammar at school didn't you ? To get POS tags for all words in the second sentence:

```kotlin
sentence.posTags()
```
```text
res3: kotlin.collections.(Mutable)List<kotlin.String!>! = [DT, VBP, DT, NNS, IN, DT, NN, NN, .]
```
