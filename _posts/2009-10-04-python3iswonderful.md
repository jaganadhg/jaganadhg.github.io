
---
layout: post
title: Python3 is wonderful
author: jagan
tags: [Python, Python3]
comments: true
---
See the below given Python code. What do you think!! will it be executed without throwing errors or not?

```python
    import sys

    def പണിയെടുക്കൂ ( പാഠം):
        for വരി in പാഠം:
            print( വരി )


    വരവ് = sys.argv[1]

    മൊത്തം = open(വരവ്,'r').readlines()

    പണിയെടുക്കൂ(മൊത്തം)

```

Don't scratch your head it will. If you use Python3 for running the code. 

Save the code as test.py. Install Python3 . Run the program as python3 test.py <your file>

I just saw some new Python documentation for Python3 with some similar examples. Thanks to Santhosh Thottingal SMC for pointing the link. Then I decided to experiment with it. 

Wow great in Python3 you can declare variable names function names in your local language. But you wont get the Python reserved words in in your language. I think Python is the first programming language which provides such a great facility. 




Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
