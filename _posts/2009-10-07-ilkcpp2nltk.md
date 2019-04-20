
---
layout: post
title: NLTK and Indian Language corpus processing Part - I
author: jagan
tags: [Natural Language Processing, NLTK, Text Processing, Python]
comments: true
---
During my presentation in [Indian Python conference](http://in.pycon.org/2009) some body asked about Indian Language corpus processing in NLTK. Some how I skipped the answer. Because I know that Indian Language corpus is there in NLTK. But I never tried to play with that. But after the conference I did some thing on that too. I am posting my experiments with results here. If it can be done in a better way please tell me so that I can improve. 

The Natural Language Toolkit contains some Indian language corpus. The corpus is  POS Tagged one. It is available for Bangala, Hindi, Marathi and Telugu languages. 

    Total number of words in Bangala is     10281
                  Hindi     9408
                  Marathi     19066
                  Telugu     9999

    Total number Sentences in Bangala     899
                  Hindi        541
                  Marathi    1197
                  Telugu    994

Let's see how to access Indian Language corpora in NLTK and how to play with it.

```python
    >>> from nltk.corpus import indian

    It will import Indian Language corpus from NLTK data.

    >>> indian.fileids() # Shows files in Indian Language corpus collection in NLTK
    ['bangla.pos', 'hindi.pos', 'marathi.pos', 'telugu.pos']
    >>> 
```

To find number of characters in each language corpora

```python
    >>> for f in indian.fileids():
    ...     print f
    ...     print len(indian.raw(f)) 
```

It will produce the following output 

    bangla.pos
    209525
    hindi.pos
    175045
    marathi.pos
    429234
    telugu.pos
    251391

To find number of words in each language corpus 

```python
    >>> for f in indian.fileids():
    ...     print f
    ...     print len(indian.words(f))
    ... 
```

It will produce the following output 

    bangla.pos
    10281
    hindi.pos
    9408
    marathi.pos
    19066
    telugu.pos
    9999

To find number of sentences 

```python
    >>> for f in indian.fileids():
    ...     print f
    ...     print len(indian.sents(f))
    ... 
```

It will produce the following output 
    
    bangla.pos
    899
    hindi.pos
    541
    marathi.pos
    1197
    telugu.pos


We can extract sentences from these corpora too.

For accessing sentences from Hindi corpus 
    `>>> hindi_sent = indian.sents('hindi.pos')`

To print individual sentences 

```python
    >>> for hsen in hindi_sent:
        print hsen
```

It will print each sentence as a list of words. Let's see how store sentences to a file. 

```python
    >>> it = open("jhi.txt",'w')
    >>> for hsen in hindi_sent:
    ...     it.write(" ".join(hsen))
    ... 
```

The above given piece of code will convert the list of words in to actual sentence, and it will store to the file specified.


To access words in a corpus 

    `>>> hin_word = indian.words('hindi.pos')`

This piece of code will store all the words in hindi.pos file to hin_words.


As we stored the sentences in to file we can write words to file also.

```python
    >>> hwo = open("hcwo.txt",'w') # Open a file to store the words
    >>> for hw in hin_word:
    ...     hwo.write(" ".join(hw)) # Write each words to the file
    ...
```

For accessing the POS tagged sentences from a corpora

```python
    >>> hpos = indian.tagged_sents('hindi.pos')

    >>> for sent in hpos:
    ...    print sent
```

It will print the POS tagged sentences a list of tuples.

More coming soon !!!!!

Happy hacking


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
