---
layout: post
title: Taming Text - Review
tags: [Natural Language Processing, Text Mining, AI, Machine Learning, Computational Linguistics, Search Engine, Apache Mahout, Book Review]
use_math: true
comment: true
---
   We are living in the era of Information Revolution. Everyday wast amount of information is being created and disseminated over World Wide Web(WWW). Even though each piece of information published in the web is useful in some way; we may require to identify and extract relevant/useful information.Such kind of information extraction includes identifying Person Names, Organization Names etc.. ,finding category of a text, identifying sentiment of a tweet etc ... Processing large amount text data from web is a challenging task, because there is an information overflow. As more information appears there is a demand for smart and intelligent processing and text data. The very field of text analytics has been attracted attention of developers around the glob. Many practical as well as theoretical books has been published on the topic. 

This book, ["Taming Text"](https://www.manning.com/books/taming-text), written by Grant S. Ingersoll, Thomas S. Morton and Andrew L. Farris is an excellent source for Text Analytics Developers and Researchers who is interested to learn Text Analytics. The book focuses on practical Text Analytics techniques like Classification,Clustering, String Matching, Searching and Entity Identification. The book provides easy-to follow examples in using well-known Open Source Text Analytics tools like Apache Mahout, Apache Lucece, Apache Solr, OpenNLP etc.. The entire book is based on the author's experience in contributing to relevant Open Source tools, hands on experience and their industry exposure. It is a must-read for Text Analytics developers and Researchers. Given the increasing importance of Text Analytics this book can be served as a hand book for budding Text Analytics Developers and Industry People. Definitely it can be used in Natural Language Processing, Machine Learning and Computational Linguistics courses. 

Chapter 1: Getting Started Taming Text
The first chapter of the book introduces what is Taming Text? The authors gives list of challenges in text processing with brief explanations. The chapter is mostly an introductory stuff. 

Chapter 2: Foundations of Taming Text
This chapter gives a quick warm up of your high school English grammar. Starting from words, the authors presents essential linguistic concepts required for text processing.  I think "Taming Text" will be the first technical book which gives a good warm up on basics of Language and grammar. The chapter gives a detailed introduction to words, parts of speech, phrases and morphology. This introduction is sufficient enough to capture the essential linguistic aspects of Text Processing for a developer. The second part of this chapter deals with basic text processing tasks like, tokenization, sentence splitting, Part of Speech Tagging (POS Tagging) and Parsing. Code snippets for each of the task has been given in the chapter. All the code examples are narrated with the tool OpenNLP . The chapter gives some basic of handling different file formats using [Apache Tika](http://tika.apache.org/). This chapter gives a step by step intro to the preliminaries of Text Processing. 

Chapter 3: Searching
This chapter introduces the art of Search. It gives a brief but narrative description of the Search mechanism and scene behind the curtains. The chapter discusses the basics of Search with the help of [Apache Solr](http://lucene.apache.org/solr/). There is an interesting discussion on search evaluation and search performance enhancements and page rank too. The chapter gives a detailed list of Open Source search engines. But I think the authors forgot to add the ["Elasticsearch"](http://www.elasticsearch.org/) library  to the list. I hope that it may be added in the final print version of the book. 

Chapter 4: Fuzzy String Matching
Everybody might have wondered how the "Did you mean:" feature in Google or any other search engine works. Long ago I saw a question in Stackoverflow; querying about the availability of source code for  "Did you mean:" feature !!! (something similar I think). If you wonder how this feature is working this chapter will give you enough knowledge to implement something similar. There is a simple discussion on different fuzzy string matching algorithms with code samples. There is practical examples on how to implement the "Did you Mean" and type ahead (auto suggest) utility on Apache Solr. Over all this chapter gives a solid introduction and hands on experience on Fuzzy String Matching. 

Chapter 5: Identifying People, Places and Things
Diving deeper into text processing ocean, the authors narrates many deeper concepts in Text Processing starting from this chapter. The main focus of this chapter is Named Entity Identification (NER), one of the trivial tasks in Information Extraction and Retrieval. The chapter gives a good introduction to the task on Named Entity Identification along with code samples using [OpenNLP](http://incubator.apache.org/opennlp). The code samples will help you to make your hands dirty. There is a section which deals with how to train OpenNLP to adopt a new domain. This will be one of the most useful tip for working professionals. The only thing which I feels to be missing is a mention about [GATE](http://gate.ac.uk/) and [Apache UIMA](http://uima.apache.org/). Both of the tools are famous for their capability to accomplish the NER task. 

Chapter 6: Clustering Text
The sixth chapter mainly deals with Clustering. Clustering is an unsupervised (i.e. no human intervention required) task that can automatically put related content into buckets.[Taken from the book "Taming Text"]. The initial part of this chapter narrates clustering with reference to real world applications. A decent discussion on clustering techniques and clustering evaluation is also there. Code examples for clustering is given in this chapter. [Apache Solr](http://lucene.apache.org/solr/), [Apache Mahout](http://mahout.apache.org/) and [Carrot](http://project.carrot2.org/) are used to give practical examples for clustering. 

Chapter 7: Classification, Categorization and Tagging 
Seventh chapter deals with document classification. As like in the other chapters there is a reasonable discussion on document classification techniques. This chapter will teach you how to perform document classification with Apache Lucene, Apache Solr, Apache Mahout and OepnNLP. There is interesting project called 'tag recommender' in this chapter. The only hiccup which I faced with this chapter is the "TT_HOME" environment variable which used through out the book. I think the authors forgot to mention how to set TT_HOME. I was familiar with Apache Mahout so ther was no issue with MAHOUT_HOME environment variable. A totally newbie will find it difficult to spot the TT_HOME and MAHOUT_HOME used in the code samples. A little bit light on setting these variables may help reader a lot. I think this will be included in the final copy(I am reading a MEAP version).

Chapter 8: An Example Application: Question Answering
This chapter gives a hands on experience in Taming Text. The entire chapter is dedicated for building a Question Answering project using the techniques discussed in all the chapters. A simple make your hands dirty by Taming Text chapter. Here also you will be caught with the TT_HOME ghost.

Chapter 9: Untamed Text: Exploring the Next Frontier
The last chapter "Untamed Text: Exploring the Next Frontier" mentions other ares in Text processing such as Semantics Pragmatics and Sentiment Analysis etc.. Brief narration on each of these field are included in this chapter. There are a lots of pointers to some useful tools for advanced Text processing tasks like Text Summarisation and Relation Extraction etc .. 

Conclusion
Grant S. Ingersoll, Thomas S. Morton and Andrew L. Farris have done a nice job by authoring this book with lucid explanations and practical examples for different Text Processing Challenges. With the help of simple and narrative examples the authors demonstrates how to solve real world text processing challenges using Free and Open Source Tools. The algorithm discussions in the book is so simple; even a newbie can follow the concepts without much hiccups. It is a good desktop reference for people who would like to start with Text Processing. It provides comprehensive and hands-on experience in Text Processing. So grab a copy soon and be ready for Big Data Analysis. 

Free and Open Source Tools Discussed in the Book
[Apache Solr](http://lucene.apache.org/solr/)
[Apache Lucene](http://lucene.apache.org/)
[Apache Mahout](http://mahout.apache.org/)
[Apache OpenNLP](http://incubator.apache.org/opennlp/)
[Carrot2](http://project.carrot2.org/). 

Disclaimer : I received a review copy of the book from Manning 


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
