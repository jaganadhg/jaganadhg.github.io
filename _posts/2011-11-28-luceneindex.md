---
layout: post
title: Lucene Index Writer API changes from 2.x to 3.x
tags: [Search Engine, Apache Lucene]
use_math: true
---
The 3.x version of Lucene introduces lots of changes in its API. In 2.x we used IndexWriter API like this:
       
```java
         Directory dir = FSDirectory.open(new File(indexDir));
        writer = new IndexWriter(dir,new StandardAnalyzer(Version.LUCENE_30),true,IndexWriter.MaxFieldLength.UNLIMITED);
```

I used the same code with 3.x version for one of my project. The tool was working fine. But my IDE(eclipse) told that some of the things are deprecated hmm...... I decided to dig the new API and I found that the above given code has to be changed to this :

```java
        Directory indexDir =  FSDirectory.open(new File(strDirName));
        IndexWriterConfig confIndexWriter = new IndexWriterConfig(Version.LUCENE_CURRENT, analyzer);
        writer = new IndexWriter(indexDir, confIndexWriter); 
```

If you would like to use the `"IndexWriter.MaxFieldLength.UNLIMITED"` the `IndexWriterConfig` should be like:
        ```j
        ava IndexWriterConfig idxconfa = new IndexWriterConfig(Version.LUCENE_30, new LimitTokenCountAnalyzer(new StandardAnalyzer(Version.LUCENE_30), 1000000000));
        ```

The int '1000000000' is set as maximum limit here. `max(int)` is the maximum you can set in `IndexWriterConfig`.


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
