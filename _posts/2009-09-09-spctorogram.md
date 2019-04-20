
---
layout: post
title: Plotting wave form and spectrogram the pure Python way
author: jagan
tags: [Python, Speech Processing, Natural Language Processing]
comments: true
---
In one of my earlier post we discussed [how to plot spectrogram with 'scikits audiolab' and python](http://jaganadhg.github.io/spectrogram/). One of my friend asked me whether it is possible to do without 'audiolab'. So I started exploring Python wave reading module and wrote another piece of code to plot spectrogram and waveform. In this program I reduced some dependency also. While using 'audiolab',  'numpy' and 'struct' were imported in the program. In this program only 'pylab' and 'wave' modules are imported. This program will plot both waveform and spectrogram in same window. 
Here is the code.

```python
#!/usr/bin/env python
import sys
from pylab import *
import wave

def show_wave_n_spec(speech):
    spf = wave.open(speech,'r')
    sound_info = spf.readframes(-1)
    sound_info = fromstring(sound_info, 'Int16')

    f = spf.getframerate()
    
    subplot(211)
    plot(sound_info)
    title('Wave from and spectrogram of %s' % sys.argv[1])

    subplot(212)
    spectrogram = specgram(sound_info, Fs = f, scale_by_freq=True,sides='default')
    
    show()
    spf.close()

fil = sys.argv[1]

show_wave_n_spec(fil)
```

To run the program copy and paste the code into a file sp.py. Run python sp.py your_wav.wav .

I just run the program on a small .wav file . The result is shown below.




Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
