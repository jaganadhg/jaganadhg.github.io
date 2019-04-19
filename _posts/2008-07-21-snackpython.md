---
layout: post
title: The Snack toolkit with Python
tags: [Python, Speech Processing]
use_math: true
comment: true
---
Snack is a toolkit for creating powerful multi-platform audio applications. With just few lines we can create some applications. The tool is developed by Speech, Music and Hearing part of [School of Computer Science and Communication, Royal Institute of Technology (KTH)](http://www.speech.kth.se/snack/index.html), Sweden. We can write applications in Tcl/Tk or in Python. 

For the last two years I was trying to properly install it in a Fedora core 8 machine. It showed so many errors. Finally I decoded to drop the plan to play with Snack :-). 

Today again I tried snack with Ubuntu9.0.4 (Jaunty Jackalope). It was successful. Please follow the below given instructions to install Snack on Ubuntu9.0.4.

    1)  sudo apt-get install libsnack2
    2) sudo apt-get install libsnack2-dev
    3) sudo apt-get install libsnack2-alsa
    4) sudo apt-get install python-tksnack 

A small [tutorial](http://www.speech.kth.se/snack/man/snack2.2/python-man.html) cum guide is available for Snack Python programming. I just tried to plot signal and spectrogram with Sansk and Python. To do the same you have to record some utterence and save it as .wav file. Ytterence means speak a word or two or more (As you like).
Then start python interpreter and type the following line one by one. Dont copy paste and make file to run it. It wont work(I dont know why!!).

```python
 >>> from Tkinter import *
>>> import tkSnack
>>> root = Tk()
>>> tkSnack.initializeSnack(root)
>>> mysound = tkSnack.Sound()
>>> mysound.read('/home/jaganadh/Desktop/syllables.wav') ## Here you have to give the file name of your wav file.
>>> c = tkSnack.SnackCanvas(root, height=400)
>>> c.pack()
>>> c.create_waveform(0,0, sound=mysound, height=100, zerolevel=1)
1
>>> c.create_spectrogram(0,150,sound=mysound, height=200)
2
>>> 
```

The result is like this.


I will make more experiments with this tool and will post.
Happy hacking !!!!!!!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
