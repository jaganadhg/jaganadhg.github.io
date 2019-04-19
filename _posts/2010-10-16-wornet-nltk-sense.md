layout: post
title: WordNet sense similarity with NLTK : some basics 
tags: [Python, Natural Language Processing, Computational Linguistics, NLTK,AI]
use_math: true
comments: true
---

The [Natural Language Tool Kit](nltk.org) (NLTK) has a WordNet module which enables a developer to play around with it in different ways. Recently I saw a question regarding Word Sense Disambiguation with NLTK. I just planed to try finding sense similarity. NLTK has implementation of the following sense similarity algorithms. 

1) Wu-Palmer Similarity:
Return a score denoting how similar two word senses are, based on the depth of the two senses in the taxonomy and that of their Least Common Subsumer (most specific ancestor node).
2) Resnik Similarity:
Return a score denoting how similar two word senses are, based on the Information Content (IC) of the Least Common Subsumer (most specific ancestor node).

3) Path Distance Similarity:
Return a score denoting how similar two word senses are, based on the shortest path that connects the senses in the is-a (hypernym/hypnoym) taxonomy.
4) Lin Similarity:
Return a score denoting how similar two word senses are, based on the Information Content (IC) of the Least Common Subsumer (most specific ancestor node) and that of the two input Synsets.
5) Leacock Chodorow Similarity:
Return a score denoting how similar two word senses are, based on the shortest path that connects the senses (as above) and the maximum depth of the taxonomy in which the senses occur.
6) Jiang-Conrath Similarity:
Return a score denoting how similar two word senses are, based on the Information Content (IC) of the Least Common Subsumer (most specific ancestor node) and that of the two input Synsets.

(Description taken from the NLTK help guide)

I just wrote a small piece of code to find Path Distance Similarity and Wu-Palmer Similarity. IT returns all the score by comparing all the sysnsets of two given words.

The code is available at my [bitbucket repo](http://bitbucket.org/jaganadhg/blog/src/d4f9b6091a9b/wnsim/wn-similar.py)

```python
#!/usr/bin/env python



from nltk.corpus import wordnet as wn



def getSenseSimilarity(worda,wordb):

	"""

	find similarity betwwn word senses of two words

	"""

	wordasynsets = wn.synsets(worda)

	wordbsynsets = wn.synsets(wordb)

	synsetnamea = [wn.synset(str(syns.name)) for syns in wordasynsets]

	synsetnameb = [wn.synset(str(syns.name)) for syns in wordbsynsets]



	for sseta, ssetb in [(sseta,ssetb) for sseta in synsetnamea\

	for ssetb in synsetnameb]:

		pathsim = sseta.path_similarity(ssetb)

		wupsim = sseta.wup_similarity(ssetb)

		if pathsim != None:

			print "Path Sim Score: ",pathsim," WUP Sim Score: ",wupsim,\

			"\t",sseta.definition, "\t", ssetb.definition



if __name__ == "__main__":

	#getSenseSimilarity('cat','walk')

	getSenseSimilarity('cricket','score')

```

The code is available at my [bitbucket repo](http://bitbucket.org/jaganadhg/blog/src/d4f9b6091a9b/wnsim/wn-similar.py)



Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
