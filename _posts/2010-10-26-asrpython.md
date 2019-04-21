---
layout: post
title: Speech Recognition with Python
author: jagan
tags: [Python, Speech Recognition, ASR, Automatic Speech Recognition]
comments: true
---

Recently I saw a [talk in listed in the CMU Sphinx site](http://cmusphinx.sourceforge.net/2010/07/pocketsphinx-talk-on-pycon/) about Speech recognition with Python and Pocket Sphinx. I have downloaded the video and replicated the experiments. It was successful . To play with Python and speech recognition we have to install the following packages.
python-pocketsphinx
pocketsphinx-lm-wsj
pocketsphinx-hmm-wsj 

These three packages are available in the Ubuntu repo. So using apt-get install you can install it. 

If you are using fedora install the following packages with yum :

```bash
pocketsphinx-devel
pocketsphinx-libs
pocketsphinx-plugin
pocketsphinx-python
pocketsphinx 
```

The language model and hmm files are not available in the fedora repo so I downloaded the source files from [http://packages.ubuntu.com/en/maverick/pocketsphinx-lm-wsj](http://packages.ubuntu.com/en/maverick/pocketsphinx-lm-wsj) and http://packages.ubuntu.com/fi/maverick/pocketsphinx-lm-wsj .

Then following the instruction in the video I prepared a python code. To test the code I used wav files from NLTK data (timit corpus). 

The python code which I used is given below
The code is available at my bitbucket "[http://bitbucket.org/jaganadhg/blog/src/tip/asr/asr.py](http://bitbucket.org/jaganadhg/blog/src/tip/asr/asr.py)"


```python
#!/usr/bin/env python

import sys,os



def decodeSpeech(hmmd,lmdir,dictp,wavfile):

	"""

	Decodes a speech file

	"""

	try:

		import pocketsphinx as ps

		import sphinxbase

	except:

		print """Pocket sphinx and sphixbase is not installed

		in your system. Please install it with package manager.

		"""

	speechRec = ps.Decoder(hmm = hmmd, lm = lmdir, dict = dictp)

	wavFile = file(wavfile,'rb')

	wavFile.seek(44)

	speechRec.decode_raw(wavFile)

	result = speechRec.get_hyp()



	return result[0]



if __name__ == "__main__":

	hmdir = "/home/jaganadhg/Desktop/Docs_New/kgisl/model/hmm/wsj1"

	lmd = "/home/jaganadhg/Desktop/Docs_New/kgisl/model/lm/wsj/wlist5o.3e-7.vp.tg.lm.DMP"

	dictd = "/home/jaganadhg/Desktop/Docs_New/kgisl/model/lm/wsj/wlist5o.dic"

	wavfile = "/home/jaganadhg/Desktop/Docs_New/kgisl/sa1.wav"

	recognised = decodeSpeech(hmdir,lmd,dictd,wavfile)

	print "%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%"

	print recognised

	print "%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%"

```


Happy Hacking

Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
