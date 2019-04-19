---
layout: post
title: How to plot spectrogram with Python
tags: [Python, Speech Processing]
use_math: true
comment: true
---
To read more about spectrogram please see [http://en.wikipedia.org/wiki/Spectrogram](http://en.wikipedia.org/wiki/Spectrogram).
Here I am going to demonstrate how to plot spectrogram with Python and audiolab.
Noramally people who is working in Speech processing will be plotting spectrogram with ['Praat'](http://www.fon.hum.uva.nl/praat/) or ['wavesurfer'](http://www.speech.kth.se/wavesurfer/) or ['Speech Analyser](http://www.sil.org/computing/sa/index.htm) (Not Open Source)'. Some advanced users will be writing [Matlab](http://www.mathworks.com/) scripts to deo the same. It is possible to do the same with python also. 

The requirements for this script are listed below.

    1) Python 2.5 or >
    2) Scipy
    3) Pylab
    4) numpy
    5) Audiolab

If these modules are not available in your system download and install it. Except audiolab everything else can be installed with apt in Ubuntu. 
`
if everything == "ok":
    print "copy the script and start"
else:
    print "please complete setup and do it"
`
(This is not a code. Just for fun I written like this)


so everything is Ok. Then copy the below given script and save it to a file called '`spc.py`'. Get a word recorded and stored in .wav format. Run the script as '`python spc.py <your wavefile>`'. It will plot the spectrogram, you can save it also.

```python
#!/usr/bin/env python
import sys
from scipy import *
from pylab import *
from numpy import *
import scikits.audiolab as audiolab
import struct

def show_Specgram(speech):
    '''
    Reads .wav file from STDIN and plots the spectrogram
    '''
    sound = audiolab.sndfile(speech,'read')
    # Reads wav file with audiolab
    sound_info = sound.read_frames(sound.get_nframes())
    # Extracts feature info from sound file with scipy module
    spectrogram = specgram(sound_info)
    #Generates soectrogram with matplotlib specgram
    title('Spectrogram of %s'%sys.argv[1])
    show()
    sound.close()
    return spectrogram 


file = sys.argv[1]
show_Specgram(file)

```

See the spectrogram which I plotted from a .wav file.


I got fragments of code from net. I am not remembering all the sources. Any how I acknowledge thanks to those people and Google.

Happy hacking!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
