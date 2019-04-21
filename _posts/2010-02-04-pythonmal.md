---
layout: post
title: Again Python programming in Malayalam
author: jagan
tags: [Python, Python3]
comments: true
---

I tried Object Oriented Programming in Python (Python3) with Malayalam class names and variable names.

See the code. It works very well with Python3 interpreter.

```python
    class പക്ഷി:

        def __init__(self):
            """
            ക്ലാസ് ഇനിഷ്യലൈസേഷന്‍
            """
            self.വിവിധ = ['കാക്ക','പ്രാവ്','കുരുവി','തത്ത','മൈന','പരുന്ത്','മൂങ്ങ']

        def പറക്കുക(self, ഇനം):
            """
            പറക്കുമോന്ന് നോക്കാല്ലോ!!!!!!!!!!!
            """
            if ഇനം in self.വിവിധ:
                print("%s പറക്കുന്ന പക്ഷിയാണ്" % ഇനം)
            else:
                print("എനിക്കറിയാമ്മേലേ!!!!!!")

    if __name__ == "__main__":
        സൂചകം = പക്ഷി()
        പറവ = "കാക്ക"
        മൃഗം = "ആന"
        സൂചകം.പറക്കുക(പറവ)
        സൂചകം.പറക്കുക(മൃഗം)
```
Use Python3 interpreter to run the code !!!!


Happy Hacking !!!!!!!

Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
