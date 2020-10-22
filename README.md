# Stanford CoreNLP Python Wrapper
Python wrapper for [Stanford CoreNLP](https://stanfordnlp.github.io/CoreNLP/index.html) that interfaces with the [Stanford CoreNLP server](https://stanfordnlp.github.io/CoreNLP/corenlp-server.html).
It provides a simple API for text processing tasks such as Tokenization, Part of Speech Tagging, Named Entity Reconigtion, Constituency Parsing, Dependency Parsing, as described in the [Full List Of Annotators](https://stanfordnlp.github.io/CoreNLP/annotators.html).

## Prerequisites
* Java 1.8+ ([Download Page](https://www.java.com/en/)). You can check java version with the command: `java -version`.
* Python 3.6+ ([Download Page](https://www.python.org/downloads/)). You can check python version with the command: `python --version`.
* Stanford CoreNLP files version 4.1.0 ([Download Page](http://nlp.stanford.edu/software/stanford-corenlp-4.1.0.zip)).

## Usage
### Annotators wrapper - Simple Usage - Using local files
This example demonstrate how to use the annotators wrapper using the local files downloded from [Stanford CoreNLP](http://nlp.stanford.edu/software/stanford-corenlp-4.1.0.zip).

All the annotators and their information can be found in [Stanford CoreNLP Full List Of Annotators](https://stanfordnlp.github.io/CoreNLP/annotators.html).
```python
from StanfordCoreNLP import StanfordCoreNLP

with StanfordCoreNLP('stanford-corenlp-4.1.0') as nlp:
    print('Tokenize:', nlp.tokenize("Hello world. Hello world again."))
    print('Sentence Splitting:', nlp.ssplit("Hello world. Hello world again."))
    print('Part of Speech:', nlp.pos("Marie was born in Paris."))
```
