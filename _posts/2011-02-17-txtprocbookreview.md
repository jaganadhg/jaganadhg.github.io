---
layout: post
title: Book Review : Python 2.6 Text Processing Beginner's Guide by Jeff McNei
tags: [Book Review, Text Processing, Natural Language Processing, Python, Packt,PyLucene]
use_math: true
comment: true
---
![Book Cover](http://link.packtpub.com/41TW0o) [Python 2.6 Text Processing Beginner's Guide](http://link.packtpub.com/41TW0o) by Jeff McNeil is one of the latest books by Packt Publishers. I received the review copy of this book before one and half months or so. Due to busy schedule I was not able to finish the review process. Finally I got enough time to review it. The book gives good insight to on different technical aspects and use of Python standards and third party libraries for text processing. It is filled with lots of examples and practical projects. I think I might have took almost one year to gather knowledge in  the topic discussed in this book, when I started my career in Natural Language Processing domain. I am giving a bit detailed review on the book here. 

The first chapter of this book gives some practical and interesting exercises like implementing cypher, some basic tricks with HTML. It also discusses how to setup a Python virtual environment for working with the examples in the book. The section of setting virtual environment is nice an well written one. It gives a clear idea of how to setup virtual environments. 

The second chapter deals with Python IO module. It narrates the basic file operations with Python. The use of context manager(with function) for for file processing is discussed in this chapter. I am suing Python for text processing for lat three to four years. But after reading only I found that there is something called "fileinput" in Python programming language for multiple file access. The chapter discuss how to access remote files and StringIO() module in Python. At the end of this chapter there is a discussion about IO in Python 3 too.

The third chapter is about Python String Services. It deals with string formatting, templating, modulo formatting etc. Every concept is explained with necessary mini projects which followed from chapter two. The chapter gives a comprehensive view on advanced string services in Python.

The fourth chapter is entitled as Text Processing Using the Standard Library. This chapter deals with topic like reading wnd writing csv files(csv file processing), playing with application config files(.ini files), and working with JSON. The examples are bit long one but worth practicing for better understanding. 

The fifth chapter deals with one of the key aspect in text processing "Regular Expressions". The chapter teaches basics syntax of regular expression in Python. The chapter also discusses about advanced processing like regex grouping, look ashed and look behind assertion in regular expressions. The look behind operation in regular expression is the most tricky part in dealing with regex. I think only masters in regex can do it effectively ;-) .The chapter dscuss basics of Unicode regular expressions too. The chapter is filled with enough examples for each and every concept discussed.

The sixth chapter deals with Markup Languages. The chapter discusses about XMl and HTML processing with Pytho standard libraries. xml.dom.minido, SAX,laxm and BeautifulSoup packages are discussed with illustrative examples. 

The seventh chapter is entitled as Creating Templates. "Templating involves the creation of text files, or templates, that contain special markup. When a specialized parser encounters this markup, it replaces it with a computed value". The templating concept was quite new to me. But I got a good insight on the topic from this chapter. The chapter discusses some libraries like "Makeo" for templating task.

The eight chapter deals with localization (l1on) and encoding. If you are working with non-English data this chapter is a must read for you.The chapter discuses about character encoding, Unicode processing and Python3 too. Apart from mere Python stuff this chapter gives a good insight about charter encoding too. 


The ninth chapter Advanced Output Formats is quite useful if you are trying to create output in PDF, CSV orExcel format. This chapter discuss about ReportLab a PDF generation library in Python.The only disadvantage which I found in ReportLab is its lack of complete Unicode Support. The chapter also discusses about creating excel files with xlwt module. Finally the chapter deals with handling OpenDocument format woth ODFPy module too. I used to read excel file from Python. But after going through this book I am able to even write Excel output too.

The tenth chapter deals with Advanced Parsing and Grammars. This is one of the key skill which required for Python text processing peoples. Creating custom grammars for parsing specific data. Through out my career I spent lot of time to train Engineers to understand parsing and BNF grammar. This time I got a good pointer for my people to start with BNF and Python programming. Also this chapter discusses about some parsing module in NLTK my favorite Python library. Some advanced topics in PyParsing also discussed in this chapter. 

The eleventh and last chapter is the most interesting one in the book. The chapter deals with Searching and Indexing. PyLucene is the bset known Searching Index library in Python. But it is a wrapper to the apache Lucene. But his chapter discusses about another Python tool Nucular. Practical examples for creating search index etc are given in this chapter. This is the first time I am using the Nucular tool. I feel it as a nice and easy one compared to PyLucene. But I dont think this is superior than Lucene. I will play more with this tool and will update it in another blog post. 

There are two appendix . The first appendix gives pointers to Python resources. The next one is answer o the pop quiz in the chapters. 

I will give 9 out of 10 for this book. If you are dealing with rigorous text processing this book is a must have reference for you.


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
