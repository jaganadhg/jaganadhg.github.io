---
layout: post
title: Quick MySQL to CouchDB migration with Python
tags: [CouchDB, Python, MySQL, Database Programming, NoSQL]
use_math: true
---
I used to play a lot with text databases. Today I was just thinking of migrating some of my data collection to CouchDB. I used the following script to convert one of my DB table (Almost all fields are TEXT) to a CouchDB collection.

```python
#!/usr/bin/env python
import couchdb
import MySQLdb as mdb
couch = couchdb.Server()
db = couch.create('YOUR_COLLECTION_NAME')
con = mdb.connect(host='HOST_NAME',user='YOU',passwd='YOUR_PASS',db='YOUR_DB')
cur = con.cursor(mdb.cursors.DictCursor)
command = cur.execute("SELECT * FROM YOUR_DB_TABLE")
results = cur.fetchall()
for result in results:
    db.save(result)
```
 
 
The DictCursor in Python MySQLdb API was a great help in creating fields and values in CouchDB collection. As my table contained text data only the operation was smooth and I was able to migrate about 1 GB data to CouchDB. But !!! life is not easy if your text data have encoding issues or junk values that can't be converted to Unicode you are in trouble. Don't worry here comes the solution; replace the last two lines in the code with below given code.

```python
for result in results:
    k = result.keys()
    v = result.values()
    v = [repr(i) for i in v]
    d = dict(zip(k,v))
    db.save(d)
```
 
Hmm so far so good. But I tried the same code with a different table where the structure is like:

```sql
+-------+--------------+------+-----+---------+----------------+
| Field | Type         | Null | Key | Default | Extra          |
+-------+--------------+------+-----+---------+----------------+
| ID    | int(11)      | NO   | PRI | NULL    | auto_increment |
| NAME  | varchar(30)  | NO   |     |         |                |
| PRICE | decimal(5,2) | NO   |     | 0.00    |                |
+-------+--------------+------+-----+---------+----------------+
```

Now the code thrown a big list of error. Life is not easy !! have to find a good solution for this ... Happy hacking !!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
