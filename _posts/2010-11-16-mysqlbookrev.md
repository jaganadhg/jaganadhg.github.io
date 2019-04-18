---
layout: post
title: Book Review- MySQL for Python (Packt) by Albert Lukaszewski
tags: [MySQL, Python, Book Review, Packt]
use_math: true
---
[MySQL for Python by Albert Lukaszewski](http://link.packtpub.com/68ats1) is a must have for all Python programmers who is working with MySQL database. It provides a comprehensive overview of MySQL Python programming. There was a lack of such a good book on MySQL + Python. Developers and newbies who is interested and working in MySQL and Python used to refer some blog posts as reference resource for Python MySQL programming. Thankfully we have a new comprehensive book on MySQL Python programming. If you are a Python programmer and novice in MySQL definitely this book will help you to get good knowledge in MySQL too. I am giving 4.5 out of 5 stars for this book.

The first chapter of the book deals with installation and configuration of mysqldb Python module. It is well written one. Even a new be can properly do the installation after reading the chapter. Installation methods for different GNU/Linux distros, and Microsoft Windows is explained in this chapter. First time I am reading such an extensive installation introduction in any books. The chapter also discuss basics of MySQL DB programming with Python. 

The second chapter deals with query formation, passing query to MySQL, dynamic query processing and applying user defined variables in MySQL query. If you created a MySQL database which mentioned in chapter and follows it you may fell in to trouble here. The DB which you created is named as 'menu'; contains a table 'fish'. In second chapter also for examples this DB is quoted. But instead of "SELECT * FROM fish" the author used "SELECT * FROM menu". I am not sure is it an error or not.

The third chapter deals with the data insertion in MySQL database(Insert) . Both chapters gives basic introduction to the MySQL database and accessing MySQL database with python program. The fourth chapter deals with exception handling in MySQL Python programming. This chapter can be [downloaded from the Packt website](https://web.archive.org/web/20110901044247/https://www.packtpub.com/sites/default/files/0189OS-Chapter-4-Exception-Handling.pdf) for free. It contains concise description of error handling mechanism in python-mysqldb module. It discusses about six types of database errors and how to handle it in MySQL DB Python programming. The fifth chapter deals with fetching and processing record by record and by chunks. The sixth chapter discusses how to handle large data in MySQL python programming. It gives good examples for how to execute multiple INSERT statements rapidly. The fifth and sixth chapter gives concise idea about dynamic data insertion and retrieval from MySQL database with Python. It gives how to use the executemany() function in python-mysqldb module and the contexts when it is not be used. The seventh chapter gives a detailed picture on how to create and drop databases. It also teaches you to manage database instances with Python and database table creation automation. Eight chapter is about user management in MySQL db. This chapter discuss about user creation and access control in MySQL database with Python. Handling date and time value is discussed in chapter nine. It gives illustrative examples for frequently used functions for managing date and time with Python in MySQL. 

Aggregate functions like COUNT(), MAX(), GROUP BY etc are discussed in chapter ten. The eleventh chapter discuss about use of WHERE, HAVING etc... and joining tables. Examples are illustrated with the help of "sakila" db. String processing in MySQL is discussed in the chapter twelve. The chapter discusses about the SUBSTRING(), CONCAT() statements. 

The 13th and 14th chapter discusses some more advanced database programming concepts. The 13th chapter discusses about accessing MySQL metadata and the 14th chapter discusses about data base backup and recovery techniques. 

Each chapters contains mini projects on the concepts discussed in the chapters. It helps the reader to make hads dirty with MySQL Python programming. The language and narration style in the book is so nice. Now there is no need to Python-MySQL developers search in the web to get tips and help. 

The book touches almost all the MySQL database programming techniques except ORM. All the examples and projects explained is is simply practically oriented. I personally worked out most of the code in the book. 

The final word. 1) This book is a must have reference in your desk if you are a Python programmer works with MySQL database.
2) If you are a Ptyhon programmer and newbie in MySQL you can gain knowledge in MySQL as well as Python MySQL programming.
3) Experienced MySQL programmers can skip many parts in each chapter. The book gives good tips than other blog and resource om MySQL python programming.
4) In-short it is bible for Python-MySQL programmers

Some issues I found in the book are:
1) The installation instructions for .rpm based system "sudo yum install " . 'sudo' is not being used by many of the experienced programmers. It seems to be a command used in debian based systems like Ubuntu.
2) In the first chapter we create a db called 'menu' with a table 'fish'. But in subsequent chapters queries are introduced as ```"SELECT * FROM menu"``` etc.. I am not sure if it is an error.
[Go today and have a copy of the book](http://link.packtpub.com/68ats1). 


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
