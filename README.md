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
Example output:
```python
Tokenize: [{'token': 'Hello', 'span': (0, 5)}, {'token': 'world', 'span': (6, 11)}, {'token': '.', 'span': (11, 12)}, {'token': 'Hello', 'span': (13, 18)}, {'token': 'world', 'span': (19, 24)}, {'token': 'again', 'span': (25, 30)}, {'token': '.', 'span': (30, 31)}]
Sentence Splitting: ['Hello world.', 'Hello world again.']
Part of Speech: [{'token': 'Marie', 'pos': 'NNP'}, {'token': 'was', 'pos': 'VBD'}, {'token': 'born', 'pos': 'VBN'}, {'token': 'in', 'pos': 'IN'}, {'token': 'Paris', 'pos': 'NNP'}, {'token': '.', 'pos': '.'}]
```

### Manual Annotators
The examples below will demonstrate how to define annotators Manualy using local files or using existing server.

Properties for using manual annotators:
* annotators: [Full List Of Annotators](https://stanfordnlp.github.io/CoreNLP/annotators.html).
* pinelineLanguage: 
* outputFormat:
#### Manual Annotators - Using local files
```python
from StanfordCoreNLP import StanfordCoreNLP

nlp = StanfordCoreNLP('stanford-corenlp-4.1.0', lang = 'en')
text = 'The small red car turned very quickly around the corner.'
pros = {'annotators' : 'ner', 'pinelineLanguage' : 'en', 'outputFormat' : 'xml'} #Named Entity Recognition example
print(nlp.annotate(text, properties = pros))
nlp.close()
```
Example output:
```python
Tokenize: [{'token': 'Hello', 'span': (0, 5)}, {'token': 'world', 'span': (6, 11)}, {'token': '.', 'span': (11, 12)}, {'token': 'Hello', 'span': (13, 18)}, {'token': 'world', 'span': (19, 24)}, {'token': 'again', 'span': (25, 30)}, {'token': '.', 'span': (30, 31)}]
Sentence Splitting: ['Hello world.', 'Hello world again.']
Part of Speech: [{'token': 'Marie', 'pos': 'NNP'}, {'token': 'was', 'pos': 'VBD'}, {'token': 'born', 'pos': 'VBN'}, {'token': 'in', 'pos': 'IN'}, {'token': 'Paris', 'pos': 'NNP'}, {'token': '.', 'pos': '.'}]
```

