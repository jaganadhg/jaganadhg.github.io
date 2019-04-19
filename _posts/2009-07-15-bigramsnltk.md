---
layout: post
title: Finding bigrams with NLTK.
tags: [Natural Language Processing, NLTK, Python, Text Processing]
use_math: true
comment: true
---
In one of my previous post we discussed how to [find bi-grams with Perl](http://jaganadhg.freeflux.net/blog/archive/2009/07/13/finding-bigrams-with-t-score-in-perl.html). Here we can see how it can be dome with Python and [NLTK](http://www.nltk.org/). NLTK is a Python based tool kit for Natural Language Programming. A [Nice book is available from O'RIELLY.](http://oreilly.com/catalog/9780596516499/), have look on it. 

There is a function available in NLTK called bigrams(). Using this function we can generate bi-grams from text given in any language. Let us see how it can be used in an English text. After that I will show how it can be used to generate bi-grams in Indic Languages.

I Assumes that you have installed NLTK in your system. For installation instructions please visit the [NLTK site](http://www.nltk.org/).

Start Python interpreter. Then type the following commands in the python interpreter. 

```python
    >>> from nltk import bigrams
```

Just we are importing bigrams function from NLTK

```python
    >>> a = "Jaganadh is testing this application"
```

Creating a string for generating bi-grams

```python
    >>> tokens = a.split()
```

Converting string in to tokens

```python
    >>> bigrams(tokens)
    [('Jaganadh', 'is'), ('is', 'testing'), ('testing', 'this'), ('this', 'application.')]
    >>> 
```

We are passing tokens to the bigrams() function. That is all folks.

When we comes to Indic or other languages it can be done in a tricky way. Because your text will be in Unicode. So we have to use 'codecs' to open and read the Unicode contents. 

Below I am giving a code for generating bigrams from a Unicode text with NLTK. Copy and paste the code to your favourite editor and save it as '`mlbigram.py`'. 

```python

#!/usr/bin/env python
import codecs
import sys
from nltk import bigrams

def gen_ML_Bigram(text):
        texfbig = codecs.open(text,'r','utf8').read()
        tokens = texfbig.split()
        ml_bigram = bigrams(tokens)
        out = codecs.open("ml_bigram.txt",'w','utf8')
        for ml in ml_bigram:
                out.write(" ".join(ml))
                out.write("\n")


inp = sys.argv[1]

gen_ML_Bigram(inp)


```

Save your Unicode contents in a text file. Run `python mlbigram.py <your_unicode_text>`. After execution the output will be stored in 'ml_bigram.txt'. The code may seem slow even if you run in a small text file, because it may take time to load NLTK.

Happy hacking!!



Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
