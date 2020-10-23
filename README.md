# Stanford CoreNLP Python Wrapper
Python wrapper for [Stanford CoreNLP](https://stanfordnlp.github.io/CoreNLP/index.html) that interfaces with the [Stanford CoreNLP server](https://stanfordnlp.github.io/CoreNLP/corenlp-server.html).
It provides a simple API for text processing tasks such as Tokenization, Part of Speech Tagging, Named Entity Reconigtion, Constituency Parsing, Dependency Parsing, as described in the [Full List Of Annotators](https://stanfordnlp.github.io/CoreNLP/annotators.html).

## Prerequisites
* Java 1.8+ ([Download Page](https://www.java.com/en/)). You can check java version with the command: `java -version`.
* Python 3.6+ ([Download Page](https://www.python.org/downloads/)). You can check python version with the command: `python --version`.
* Stanford CoreNLP files version 4.1.0 ([Download Page](http://nlp.stanford.edu/software/stanford-corenlp-4.1.0.zip)).

## Usage
### Annotators wrapper - Simple Usage - Using local files
This example will demonstrate how to use the annotators wrapper using the local files downloded from [Stanford CoreNLP](http://nlp.stanford.edu/software/stanford-corenlp-4.1.0.zip).   
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
* pinelineLanguage: [Full List Of Human Languages](https://stanfordnlp.github.io/CoreNLP/human-languages.html).
* outputFormat: [JSON, XML, Text, Serialized](https://stanfordnlp.github.io/CoreNLP/corenlp-server.html#annotate-with-corenlp-).
#### Manual Annotators - Using local files
```python
from StanfordCoreNLP import StanfordCoreNLP

nlp = StanfordCoreNLP('stanford-corenlp-4.1.0')
text = 'The small red car turned very quickly around the corner.'
pros = {'annotators' : 'ner', 'pinelineLanguage' : 'en', 'outputFormat' : 'xml'} #Named Entity Recognition example
print(nlp.annotate(text, properties = pros))
nlp.close()
```
Example output:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet href="CoreNLP-to-HTML.xsl" type="text/xsl"?>
<root>
  <document>
    <sentences>
      <sentence id="1">
        <tokens>
          <token id="1">
            <word>The</word>
            <lemma>the</lemma>
            <CharacterOffsetBegin>0</CharacterOffsetBegin>
            <CharacterOffsetEnd>3</CharacterOffsetEnd>
            <POS>DT</POS>
            <NER>O</NER>
          </token>
          <token id="2">
            <word>small</word>
            <lemma>small</lemma>
            <CharacterOffsetBegin>4</CharacterOffsetBegin>
            <CharacterOffsetEnd>9</CharacterOffsetEnd>
            <POS>JJ</POS>
            <NER>O</NER>
          </token>
          <token id="3">
            <word>red</word>
            <lemma>red</lemma>
            <CharacterOffsetBegin>10</CharacterOffsetBegin>
            <CharacterOffsetEnd>13</CharacterOffsetEnd>
            <POS>JJ</POS>
            <NER>O</NER>
          </token>
          <token id="4">
            <word>car</word>
            <lemma>car</lemma>
            <CharacterOffsetBegin>14</CharacterOffsetBegin>
            <CharacterOffsetEnd>17</CharacterOffsetEnd>
            <POS>NN</POS>
            <NER>O</NER>
          </token>
          <token id="5">
            <word>turned</word>
            <lemma>turn</lemma>
            <CharacterOffsetBegin>18</CharacterOffsetBegin>
            <CharacterOffsetEnd>24</CharacterOffsetEnd>
            <POS>VBD</POS>
            <NER>O</NER>
          </token>
          <token id="6">
            <word>very</word>
            <lemma>very</lemma>
            <CharacterOffsetBegin>25</CharacterOffsetBegin>
            <CharacterOffsetEnd>29</CharacterOffsetEnd>
            <POS>RB</POS>
            <NER>O</NER>
          </token>
          <token id="7">
            <word>quickly</word>
            <lemma>quickly</lemma>
            <CharacterOffsetBegin>30</CharacterOffsetBegin>
            <CharacterOffsetEnd>37</CharacterOffsetEnd>
            <POS>RB</POS>
            <NER>O</NER>
          </token>
          <token id="8">
            <word>around</word>
            <lemma>around</lemma>
            <CharacterOffsetBegin>38</CharacterOffsetBegin>
            <CharacterOffsetEnd>44</CharacterOffsetEnd>
            <POS>IN</POS>
            <NER>O</NER>
          </token>
          <token id="9">
            <word>the</word>
            <lemma>the</lemma>
            <CharacterOffsetBegin>45</CharacterOffsetBegin>
            <CharacterOffsetEnd>48</CharacterOffsetEnd>
            <POS>DT</POS>
            <NER>O</NER>
          </token>
          <token id="10">
            <word>corner</word>
            <lemma>corner</lemma>
            <CharacterOffsetBegin>49</CharacterOffsetBegin>
            <CharacterOffsetEnd>55</CharacterOffsetEnd>
            <POS>NN</POS>
            <NER>O</NER>
          </token>
          <token id="11">
            <word>.</word>
            <lemma>.</lemma>
            <CharacterOffsetBegin>55</CharacterOffsetBegin>
            <CharacterOffsetEnd>56</CharacterOffsetEnd>
            <POS>.</POS>
            <NER>O</NER>
          </token>
        </tokens>
      </sentence>
    </sentences>
  </document>
</root>
```

#### Manual Annotators - Using existing server
```python
from StanfordCoreNLP import StanfordCoreNLP

nlp = StanfordCoreNLP('http://corenlp.run', port = 80)
text = 'Joe Smith lives in California. He used to live in Oregon.'
pros = {'annotators' : 'lemma', 'pinelineLanguage' : 'en', 'outputFormat' : 'JSON'} #Lemmatization example
print(nlp.annotate(text, properties = pros))
nlp.close()
```
Example output:
```json
{
  "sentences": [
    {
      "index": 0,
      "tokens": [
        {
          "index": 1,
          "word": "Joe",
          "originalText": "Joe",
          "lemma": "Joe",
          "characterOffsetBegin": 0,
          "characterOffsetEnd": 3,
          "pos": "NNP",
          "before": "",
          "after": " "
        },
        {
          "index": 2,
          "word": "Smith",
          "originalText": "Smith",
          "lemma": "Smith",
          "characterOffsetBegin": 4,
          "characterOffsetEnd": 9,
          "pos": "NNP",
          "before": " ",
          "after": " "
        },
        {
          "index": 3,
          "word": "lives",
          "originalText": "lives",
          "lemma": "live",
          "characterOffsetBegin": 10,
          "characterOffsetEnd": 15,
          "pos": "VBZ",
          "before": " ",
          "after": " "
        },
        {
          "index": 4,
          "word": "in",
          "originalText": "in",
          "lemma": "in",
          "characterOffsetBegin": 16,
          "characterOffsetEnd": 18,
          "pos": "IN",
          "before": " ",
          "after": " "
        },
        {
          "index": 5,
          "word": "California",
          "originalText": "California",
          "lemma": "California",
          "characterOffsetBegin": 19,
          "characterOffsetEnd": 29,
          "pos": "NNP",
          "before": " ",
          "after": ""
        },
        {
          "index": 6,
          "word": ".",
          "originalText": ".",
          "lemma": ".",
          "characterOffsetBegin": 29,
          "characterOffsetEnd": 30,
          "pos": ".",
          "before": "",
          "after": " "
        }
      ]
    },
    {
      "index": 1,
      "tokens": [
        {
          "index": 1,
          "word": "He",
          "originalText": "He",
          "lemma": "he",
          "characterOffsetBegin": 31,
          "characterOffsetEnd": 33,
          "pos": "PRP",
          "before": " ",
          "after": " "
        },
        {
          "index": 2,
          "word": "used",
          "originalText": "used",
          "lemma": "use",
          "characterOffsetBegin": 34,
          "characterOffsetEnd": 38,
          "pos": "VBD",
          "before": " ",
          "after": " "
        },
        {
          "index": 3,
          "word": "to",
          "originalText": "to",
          "lemma": "to",
          "characterOffsetBegin": 39,
          "characterOffsetEnd": 41,
          "pos": "TO",
          "before": " ",
          "after": " "
        },
        {
          "index": 4,
          "word": "live",
          "originalText": "live",
          "lemma": "live",
          "characterOffsetBegin": 42,
          "characterOffsetEnd": 46,
          "pos": "VB",
          "before": " ",
          "after": " "
        },
        {
          "index": 5,
          "word": "in",
          "originalText": "in",
          "lemma": "in",
          "characterOffsetBegin": 47,
          "characterOffsetEnd": 49,
          "pos": "IN",
          "before": " ",
          "after": " "
        },
        {
          "index": 6,
          "word": "Oregon",
          "originalText": "Oregon",
          "lemma": "Oregon",
          "characterOffsetBegin": 50,
          "characterOffsetEnd": 56,
          "pos": "NNP",
          "before": " ",
          "after": ""
        },
        {
          "index": 7,
          "word": ".",
          "originalText": ".",
          "lemma": ".",
          "characterOffsetBegin": 56,
          "characterOffsetEnd": 57,
          "pos": ".",
          "before": "",
          "after": ""
        }
      ]
    }
  ]
}
```

## Debug
You can debug using the `logging` module in python.
This example will demonstrate how to use the `logging` module:
```python
from StanfordCoreNLP import StanfordCoreNLP
import logging

nlp = StanfordCoreNLP('stanford-corenlp-4.1.0', quiet = False, logging_level = logging.DEBUG)
text = 'The small red car turned very quickly around the corner.'
print(nlp.annotate(text)) #default annotate
nlp.close()
```
