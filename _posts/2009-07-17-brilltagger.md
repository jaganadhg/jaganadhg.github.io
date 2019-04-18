---
layout: post
title: POS Tagging with Python(Brill Tagger in Python)
tags: [Natural Language Processing, POS Tagging, NLPROC]
use_math: true
---
In my [previous post](https://web.archive.org/web/20150708103138/http://jaganadhg.freeflux.net/blog/archive/2009/07/10/pos-tagging-with-perl.html)  I demonstrated how to do POS Tagging with Perl. Being a fan of Python programming language I would like to discuss how the same can be done in Python. I downloaded Python implementation of the Brill Tagger by Jason Wiener . I just downloaded it. Nice one.

Download the program from [http://wareseeker.com/Software-Development/simple-nlp-part-of-speech-tagger-in-python-1.0.zip/200a88782](http://wareseeker.com/Software-Development/simple-nlp-part-of-speech-tagger-in-python-1.0.zip/200a88782.). Create a folder and move the .zip file to the folder. Unzip it. Open the terminal and run the MakeLex.py(Python MakeLex.py). It will create lexicon for the POS Tagger. Now you can run the NLPlib.py program(python NLPlib.py). It will show the below given result.

```python
/Desktop/postag$ python NLPlib.py 
beginning test
unpickle the dictionary
Initialized lexHash from pickled data.
Tiger ( NNP )
Woods ( NNP )
finished ( VBD )
the ( DT )
big ( JJ )
tournament ( NN )
at ( IN )
par ( NN )
```

I just created a small python script to tag a given English text file. Before using the script you have to comment lines 119 to end in the NLPlib.py file. Otherwise always you will be getting the above given output. 

```python
#!/usr/bin/env python
import sys
from  NLPlib import *
nlp = NLPlib()

def tagText(t):
        text = open(t,'r').readlines()
        for line in text:
                tokens = nlp.tokenize(line)

                tagged = nlp.tag(tokens)
                for i in range(len(tokens)):
                        print tokens[i],"(",tagged[i],")"



inp = sys.argv[1]

tagText(inp)

```

Just copy the code in to an editor. Save it as tager.py. You should run the program in the same directory where you extracted the tagger. Run it like
python tager.py <your_text>

This software is licensed under the GNU GPL Licence. If you are interested to use it commercial you have to buy a licence.


Happy hacking !!!!!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
