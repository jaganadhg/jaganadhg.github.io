---
layout: post
title: Thoughts on text mining
author: jagan
tags: [Python, Perl, Text Mining, Natural Language Processing]
comments: true
---
I was reading the book '[Practical Text Mining with Perl](https://onlinelibrary.wiley.com/doi/book/10.1002/9780470382868)' by 'Roger Bilisoly', which is published by 'Willy'. It is a nice book to learn text mining through the Perl programming language for beginners . So many practical examples are give in the text. Most of the examples are familiar to me, because I am using Perl and Python for so many years. Suddenly I thought that why cant I work out the examples in Python too!! Practical text mining with Python. I am not going to write a text book :-) . Just working out the examples in Perl and Python.

In page 22 of the book the author gives a perl code for extracting words from text. In the resulted text no punctuation marks will be there. I am reproducing the code (Not the exact code in the text book.)

```perl
#!/usr/bin/env perl

$f = $ARGV[0];
open( FILE, $f ) or die("File not found or can't read\n");
while (<FILE>) {
    chomp;
    @words = split(/\s+/);
    foreach $word (@words) {
        if ( $word =~ /(\w+)/ ) {
            print "$1 \n";
        }
    }
}

```



The same thing can be implemented in Python in two different ways. 

```python
#!/usr/bin/env python

import sys
import re

txt = open(sys.argv[1],'r').read()
words = txt.split()

for word in words:
    cword = re.search('\w+',word)
    print cword.group()

```

This code have a problem. Suppose the text contains some word like "gr8one" the program will throw error "AttributeError: 'NoneType' object has no attribute 'group'". I don't know whether it is my error :-).

So the second implementation is given below.

```python
#!/usr/bin/env python

import sys
import string

txt = open(sys.argv[1],'r').read()
for punct in string.punctuation:
    txt = txt.replace(punct," ")

words = txt.split()

for word in words:
    print word
```

Hey if you have any suggestions on the programs pleas put a comment.

Happy Hacking !!!!!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
