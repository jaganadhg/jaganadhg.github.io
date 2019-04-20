---
layout: post
title: NLTK and Indian Language corpus processing - Part-II
author: jagan
tags: [Python, Natural Language Processing, Text Processing, Text Mining]
comments: true
---
In Part-I we saw how to access Indian Language corpora in NLTK and how to play with it. Now let's see some more examples.

First we can see how to access each word with associated POS tag. (Before proceeding don't forgot to do the imports done in Part-I )

```python
    >>> for sent in hpos:
    ...    tmp = sent
    ...    for j in range(len(sent))
    ...        print " ".join(k[j])
```
It will print word with POS like

    दो QFNUM
    विकेट NN
    लिये VFM
    । PUNC
    अनवर NNP
    को PREP
    विंसेट NNP
    ने PREP
    रन NNC
    आउट NN
    किया VFM
    । PUNC
    >>> 

Let us see how to do parsing with the Indian Language POS Tagged corpus. For the purpose I am using the RegexParser available in NLTK.

```python
    >>> sentence = hpos[2]
```

I am taking the third sentence in the hindi.pos file for parsing 

```python
    >>> grammar = "NP: {<DT>?<JJ>*<NN>}"
```

Defined grammar for parsing with RegexParser in NLTK.

```python
    >>> cp = nltk.RegexpParser(grammar) # Creating the parser object and passing the grammar to it
    >>> result = cp.parse(sentence) # Do the parsing and store the result to 'result'
    >>> print result # Printing the result
```

It will produce the parse structure like

    (S
      इराक/NNP
      के/PREP
      विदेश/NNC
      (NP मंत्री/NN)
      ने/PREP
      अमरीका/NNP
      के/PREP
      उस/PRP
      (NP प्रस्ताव/NN)
      का/PREP
      मजाक/NVB
      उड़ाया/VFM
      है/VAUX
      ,/PUNC
      जिसमें/PRP
      अमरीका/NNP
      ने/PREP
      संयुक्त/NNC
      (NP राष्ट्र/NN)
      के/PREP
      (NP प्रतिबंधों/NN)
      को/PREP
      (NP इराकी/JJ नागरिकों/NN)
      के/PREP
      लिए/PREP
      कम/INTF
      हानिकारक/JJ
      बनाने/VNN
      के/PREP
      लिए/PREP
      कहा/VFM
      है/VAUX
      ।/PUNC)

If you would like to visualise the parse structure just do this much 

   ` >>> result.draw()`

It will show a big parse tree. It is too big one so I am not attaching the screen shot.


Then what about generating bigrams from Indian Language corpora?

Here comes the code for that.

```
    >>> hinw = indian.words('hindi.pos') # Stores the words in 'hindi.pos' to hinw

    >>> hinbi = nltk.bigrams(hinw) # Generate the bigrams and store it in to hinbi
```

To print the bigrams

```
    >>> for i in hinbi:
    ...     print " ".join(i)
```

Here you can see some sample bigram 

    चुके थे
    थे तथा
    तथा ३
    ३ बार
    बार विधानसभा
    विधानसभा के
    के सदस्य


    
Fine then what about trigrams.
Hmmm it is easy !!

First store words in the corpus to a list

    ```>>> hinw = indian.words('hindi.pos')```

Then generate trigrams with nltk.trigrams() function 

    ```>>> hintr = nltk.trigrams(hinw)```

To print the trigrams 

```python
    >>> for j in hintr:
    ...    print " ".join(j)
```

Here is the sample output

    दो-दो तथा फ्रैंक्लीन
    तथा फ्रैंक्लीन और
    फ्रैंक्लीन और हैरिस
    और हैरिस ने
    हैरिस ने एक-एक
    ने एक-एक विकेट
    एक-एक विकेट लिये
    विकेट लिये ।


Finding count of a particular word in Indian Language corpus.

Store the words to some variable and use the count() function. 

```python
    >>> txt2 = indian.words('hindi.pos')
    
    >>> txt2.count('भारत')
    23
    >>>
```

Here I stred all the words in 'hindi.pos' and explored the count of the word भारत .

Find he percentage of text taken by a particular text

To find out the percentage of text taken by the word भारत 

```python
    >>> 100 * txt2.count('की') /len(txt2)
    2
    >>>
```

Producing lexical dispersion plot from Indian Language corpus

For that we have to play some trick

This is the command for plotting lexical dispersion plot of भारत  and की in Hindi corpus

```
    Text(txt2).dispersion_plot(['भारत','की'])
```

The Text() function convert the wordlist to nltk text object. It makes the plotting job easy. In the plot you cant see the word, because Unicode text will be displayed as box in the plot.


Selecting word based on parameters from Hindi corpus

For the same I am taking the example mentioned in the NLTK book.


    {w|w is a member of V and P(w)}

    [w for w in V if p(w)]

```python
    >>> V = set(txt2)
    >>> my_word = [w for w in V if len(w) > 25]
    >>> sorted(my_word)
    >>> fd = FreqDist(txt2)
    >>> sorted([w for w in set(txt2) if len(w) > 5 and fd[w] > 25])
```

It will give the following list of word as output

        इस
        एक
        और
        कर
        कहा
        का
        कि
        किया
        ......



Conditional frequency distribution for Indian Language corpora

Here is an example

    Step 1
    Generate bigrams

    `>>> hinbi = nltk.bigrams(hinw)`

    Step 2
    Generate Conditional Frequency Distribution 

    `>>> gd = nltk.ConditionalFreqDist(big)`

You can plot the cfd but it will take some time to generate the plot and you can see some animation effect
    
    `>>> gd.plot()`


One can print the tabulated cfd also

    `>>> gd.tabulate()`



More coming soon

Happy hacking !!!!!!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
