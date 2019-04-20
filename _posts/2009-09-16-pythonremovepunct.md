
---
layout: post
title: Python- removing punctuation from string/text
author: jagan
tags: [Python, Text Processsing]
comments: true
---
While performing one may require to remove punctuations from the text. There is an easy way to do this in Python. Using the 'string' module we can do it. 
e.g.

```python
#!/usr/bin/env python
import sys
import string

txt = open(sys.argv[1],'r').read()
for punct in string.punctuation:
    txt = txt.replace(punct,"")
print txt

```

The punctuations contained in the 'string.punctuation are 
` '!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~' `
Total 33 punctuation marks.

If you would like to retain any of the punctuation marks in the above list in your text, you can modify the loop. For example I would like to retain "%" and "$" in the text. For the same code will be like 

```python
#!/usr/bin/env python
import sys
import string

txt = open(sys.argv[1],'r').read()
excludu = ['$','%']
for punct in string.punctuation:
    if not punct in excludu:
        txt = txt.replace(punct,"")
print txt

```

Happy Hacking !!!!!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
