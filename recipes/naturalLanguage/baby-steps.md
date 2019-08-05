---
title: Baby steps
description: Explore CoreNLP's Simple API
date: 2019-08-01 00:00:00
layout: default
---

### Documents, sentences and words

Let's start by creating a [Document](https://nlp.stanford.edu/nlp/javadoc/javanlp/index.html?edu/stanford/nlp/simple/Document.html) with appropriate sample text for starting our journey. Note that this a multi-line string and we can type by hitting Enter and then Ctrl+Enter at the last line to execute.

```kotlin
val text = Document("""Space: the final frontier.
 These are the voyages of the starship Enterprise.
 Its continuing mission: to explore strange new worlds,
 to seek out new life and new civilizations,
 to boldly go where no one has gone before!""")
```

The simplest processing we can do here is split the document into [sentences](https://nlp.stanford.edu/nlp/javadoc/javanlp/index.html?edu/stanford/nlp/simple/Sentence.html) and a sentence into words. Note that it splits documents on punctuation like '.' and '!' if followed by a space and it retains the punctuation in the resulting sentences. It doesn't split on ',' or ':'. It splits sentences to words on whitespace and punctuation marks are included as words. With CoreNLP we can usually get a list of results with the plural form of a method e.g. `sentences()` or get a specific element with the singular form and a 0-based index e.g. `sentence(1)`. Try:

```kotlin
text.sentences().size
```
```text
3
```
and
```kotlin
val sentence = text.sentence(1)
```
We'll use the `sentence` variable later.

```kotlin
sentence.word(1)
```
```text
are
```

### Lemmas

While speaking we don't always use the basic, root form of a word like _go_ but other grammatically appropriate forms like _goes_ or _went_. The basic, root form is called [lemma](https://simple.wikipedia.org/wiki/Lemma_(linguistics)) and it's obvious from this example we can't always just take a substring of a word to find a lemma. We can easily find lemmas with CoreNLP with the `lemma()` method. For example the lemma of _are_, second word of second sentence is _be_:
```kotlin
sentence.lemma(1)
```
```text
be
```
To get the lemma of a single word make a sentence out of it e.g.
```kotlin
Sentence("went").lemma(0)
```
```text
go
```

### Parts of speech

CoreNLP will do its best to guess whether a word is a verb, noun, adjective etc. That is a **P**art **O**f **S**peech tag and you can learn more about these [here](https://en.wikipedia.org/wiki/Part_of_speech) and see a neat list of potential tags at [Penn tree bank](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html). You loved grammar at school didn't you? To get POS tags for all words in the second sentence:

```kotlin
sentence.posTags()
```
```text
[DT, VBP, DT, NNS, IN, DT, NN, NN, .]
```

The POS tags are in the same order as words in the sentence which can be confusing. Let's use Kotlin collections features to print pairs of words with their corresponding POS tags in separate lines:

```kotlin
sentence.posTags().zip(sentence.words()).forEach{ (pos, word) -> print("$pos\t$word\n") }
```
```text
These      DT
are        VBP
the        DT
voyages    NNS
of         IN
the        DT
starship   NN
Enterprise NN
```
To see all above lines remember to move cursor over a visible line and scroll upwards

### Graphs of word relationships

Now that we know that "final" is an adjective and "frontier" a noun, we'd like to know the relationships between words, that the adjective "final" modifies the noun "frontier" specifically in the sentence. A [Parse Tree](https://en.wikipedia.org/wiki/Parse_tree) is a good way to represent these relationships. With CoreNLP we get the constituency parse tree by calling the `parse()` method on a sentence.

```kotlin
sentence.parse().pennString()
```
```text
(ROOT
  (S
    (NP (DT These))
    (VP (VBP are)
      (NP
        (NP (DT the) (NNS voyages))
        (PP (IN of)
          (NP (DT the) (NN starship) (NN Enterprise)))))
    (. .)))
```
The output includes the words in original text, their POS tags for terminal (leaf) nodes and non terminal categories like VP (verb phrase) or NP (noun phrase) for non terminal (non leaf) nodes. Check [here](https://en.wikipedia.org/wiki/Parse_tree)) for meaning of VP, NP etc.

We may also obtain a [Semantic Dependency](https://en.wikipedia.org/wiki/Dependency_grammar#Semantic_dependencies) graph of a sentence:

```kotlin
sentence.dependencyGraph()
```
```text
-> voyages/NNS (root)
  -> These/DT (nsubj)
  -> are/VBP (cop)
  -> the/DT (det)
  -> Enterprise/NN (nmod:of)
    -> of/IN (case)
    -> the/DT (det)
    -> starship/NN (compound)
  -> ./. (punct)
```

For each node we get the original word, the POS tag and a relation according to [Universal Dependency v1](http://universaldependencies.org/docsv1/u/dep/all.html)

### Coreference Resolution

In some sentences or documents two different words may refer to the same entity. CoreNLP can perform [Coreference Resolution](https://en.wikipedia.org/wiki/Coreference#Coreference_resolution) by calling `coref()` on a `Document` or `Sentence`. Unfortunately coreference resolution is a challenging task and algorithms are not as accurate as POS tagging or parsing. For the `Document` above CoreNLP can't find that "Its" and "Enterprise" are related. This other example shows some failed and some successful resolutions:

```kotlin
Document("""To all Starfleet personel, this is the Captain. It is my sad duty to inform you that a member of the crew, 
 Ensign Sito Jaxa has been lost in the line of duty. She was the finest example of a Starfleet officer and a young woman
 of remarkable courage and strength of character. Her loss will be deeply felt by all who knew her. Picard out."""
).coref()
```
```text
{5=CHAIN5-["this" in sentence 1, "It" in sentence 2], 21=CHAIN21-["She" in sentence 3, "Her" in sentence 4, "her" in sentence 4], 13=CHAIN13-["Starfleet" in sentence 1, "Starfleet" in sentence 3]}
```
CHAIN5 is actually wrong as "this" and "It" don't refer to the same thing. The other chains are correct but it failed to spot that "She", "Her" etc are related to "Ensign Sito Jaxa".

### Named Entity Recognition

Apart from words like verbs and nouns a sentence may contain named entities that we should identify to extract useful information from our text. [Named Entity Recognition](https://en.wikipedia.org/wiki/Named-entity_recognition) may be unsuccessful if the entity and the related word are missing from the [corpus](https://en.wikipedia.org/wiki/Text_corpus) used to train the model that the NER tagging algorithm is using. For English, the algorithm is strongly influenced by the first letter being uppercase. CoreNLP performs NER tagging by calling the `nerTags` method:
```kotlin
Sentence("I'm Captain Jean-Luc Picard, of the Federation Starship Enterprise").nerTags()
```
```text
[O, O, TITLE, PERSON, PERSON, O, O, O, ORGANIZATION, ORGANIZATION, ORGANIZATION]
```
"Starship" is probably more of a VEHICLE than an ORGANIZATION so the training corpus probably didn't contain this term. "Captain" would still be identified as "TITLE" even if it was typed as "captain". Another example:
```kotlin
Sentence("Ensign Sito Jaxa has been lost in the line of duty").nerTags()
```
```text
[PERSON, PERSON, PERSON, O, O, O, O, O, O, O, O]
```
Here it successfully recognized "Sito" and "Jaxa" as names of a person despite these name being made up probably.

### Sentiment Analysis

This is a text categorisation task, an estimate if a sentence conveys a positive, negative or neutral sentiment. The underlying model used by CoreNLP is based on movie reviews. If a sentence pertains to a different domain, with different vocabulary or is rather nuanced, results can be very inaccurate. We get the sentiment of a sentence by calling the `sentiment` method. Here are some correct and not so correct results:

```kotlin
Sentence("The war is going very badly for the Federation... far worse than is generally known").sentiment()
```
```text
VERY_NEGATIVE
```
