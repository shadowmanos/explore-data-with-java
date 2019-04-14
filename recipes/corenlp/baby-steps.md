---
Baby steps
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

The simplest processing we can do here is split it into [sentences](https://nlp.stanford.edu/nlp/javadoc/javanlp/index.html?edu/stanford/nlp/simple/Sentence.html). Note that it splits on punctuation like _'.'_ and _'!'_ if followed by a space and it retains the punctuation in the resulting sentences. It doesn't split on _','_ or _':'_. With CoreNLP we can usually extract either a list with the plural form of a method or get a specific element with the singular form and an index. Try:

```kotlin
text.sentences()
val sentence = text.sentence(1)
sentence.words()
sentence.word(1)
```

### Lemmas

While speaking we transform words from the basic, root form like _"go"_ to other appropriate forms like _"goes"_ or _"went"_. The basic, root form is called [lemma](https://simple.wikipedia.org/wiki/Lemma_(linguistics)) and it's obvious from this example we can't always just take a substring of a word to find a lemma. We can easily find lemmas with CoreNLP. For example the lemma of _"are"_, second word of second sentence is _"be"_:

```kotlin
sentence.lemma(1)
``` 

### Parts of speech

CoreNLP will do its best to guess whether a word is a verb, noun, adjective etc. That is a **P**art **O**f **S**peech tag and you can see a list of potential tags 
at the [Penn tree bank](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html). You loved grammar at school didn't you ?
