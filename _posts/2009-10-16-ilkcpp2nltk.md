---
layout: post
title: NLTK and Indian Language corpus processing - Part-II
author: jagan
tags: [Python, Natural Language Processing, Text Processing, NLTK]
comments: true
---
I think you enjoyed the Part-I and Part-II of this tutorial. If you have any comment, suggestion or criticism please write to me. In part -III we can try to some more work with Indian Language Corpora in NLTK.

Generating word and POS bigram and trigram 

For generating word and POS bigram I selected the 'hindi.pos' file and created the bigrams and trigrams.
Here is the code to do that.

```python
    from nltk.corpus import indian
    from nltk import bigrams
    from nltk import trigrams

    hpos = indian.tagged_sents('hindi.pos')

    # Stores the POS tagged sentences from 'hindi.pos'

    wpos = []

    for sent in hpos:
        tojoin = sent
        for tagged in tojoin:
            wpos.append(" ".join(tagged))

    #Stores word and pos as single unit to a list called 'wpos'

    wpos_bigram = bigrams(wpos)
    # Generating word and POS bigram
    for wpb in wpos_bigram:
       print " ".join(wpb)

    # Prints the word and POS bigram

    wpos_trigram = trigrams(wpos)
    # Generating the Word and POS trigram
    for wpt in wpos_trigram:
        print " ".join(wpt)
    #Prints the word and POS trigram

```

        

For generating word and pos from other Indian Language corpus just replace 'hindi.pos' with appropriate file id.

Collocations Concordance from Indian Language Corpora

Now let's try to build collocation from hindi corpus(hindi.pos).

```python
    >>> hw = nltk.corpus.indian.words('hindi.pos')
    >>> th = Text(hw)
    >>> th.collocations()
    Building collocations list
    है ।; के लिए; कहा कि; हैं ।;
    पारी खेली; है कि; रनों की;
    न्यू जीलैंड; युद्ध विराम;
    ने कहा; के हाथों; करते हुए;
    डेविस कप; की पारी; रहे हैं;
    खेली ।; रन पर; रन बनाये;
    हाथों लपकवाया; किए गए
```

Concordence from Hindi corpus in NLTK

```python
    >>> th.concordance('न्यू')
    Building index...
    Displaying 13 of 13 matches:
    वसीय मैच में न्यू जीलैंड को जी
    ��न से बाहर कर न्यू जीलैंड की टी
    ��न सकती हैं । न्यू जीलैंड ने पा
    ती डुनेडिन । न्यू जीलैंड ने पा
    -२ से जीत ली । न्यू जीलैंड ने पा
    ��त किया गया । न्यू जीलैंड की पा
    लपकवा दिया । न्यू जीलैंड की तर
    ीसरे मैच में न्यू जीलैंड को २८
    ��े हरा दिया । न्यू जीलैंड को जी
    ��त किया गया । न्यू जीलैंड की शु
    �� पारी खेली । न्यू जीलैंड के १५
    ��ी कर पाये और न्यू जीलैंड की पा
    ोगदान दिया । न्यू जीलैंड की तर
    >>> 
```

Here is an example to populate frequency distribution of some Hindi words in 'hindi.pos' file.

```python
    # -*- coding: utf-8 -*-
    from nltk.corpus import indian
    from nltk import FreqDist
    hindi_text = indian.words('hindi.pos')
    freq_dist = FreqDist([w.strip() for w in hindi_text])
    modals = ['की','है','हो','तो']

    for modal in modals:
        print modal + " : " , freq_dist[modal]

```

The result is given below.

    की :  236
    है :  189
    हो :  28
    तो :  10


Happy Dipavali !!!
Happy Hacking 





Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
