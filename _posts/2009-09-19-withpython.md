---
layout: post
title: File handling with 'with' in Python 2.6
author: jagan
tags: [Python, with]
comments: true
---
I was exploring the online python documentation . I found an interesting way of opening and processing file content. 

For opening and getting the content from file the process will be like :

```python
        txt = open("your_file",'r') # Open file
        txtc = txt.read() # Read total content
        txt.close() # close file object 
```


You can avoid the use of file.close() if you are using the 'with' statement. 
In normal way we will be reading and printing the content like:

(1)     ```python
        txt = open("my_text.txt",'r') # Open file
        txtcont = txt.read()
        txt.close()
        print txtcont # Printing the contents of the file.
        ```

    Or
(2)     ```python
        txt = open("my_text.txt",'r') # Open file
        txtcont = txt.readlines() # Read lines from file and store to a list
        txt.close()
        
        
        for line in txtcont:
            print line # Prints line by line
        ```

The above given example can be done in another way (Copied from pydoc)
(3)   ```python
        f = open("hello.txt")
        try:
                for line in f:
                print line
        finally:
                f.close()
        ```


The items 2 and 3 can be implemented with 'with' in the following way (in Python 2.6).

```python
    with open("my_file") as txt:
        for line in txt:
            print line
```

Instead of five/six lines we are using three lines. beautiful code !!!

You may ask where is the .close() function. While using 'with' for opening a file, the opened file will be closed when the 'with' block is exited. Means the file locally scoped in the 'with' block. 

I just played with 'with' to know where all the operations which is done with normal 'open()' is possible or not. I am posting the codes below. 

```python
    import sys
    
    warr = []    
    with open(sys.argv[1]) as txt:
        txtc = txt.read()
        words = txtc.split()
        warr.extend(words)

    for wa in warr:
        print warr
```

What I tried here is open a file with 'with', split in to words and append to a list outside the scope of 'with' block, and print each element in the list.

```python
    import sys
        
    with open(sys.argv[1]) as txt:
        txtc = txt.readlines() #Read lines and store to list
        for l in txtc:
            print l # Print each line

```
Happy SFD !!!!!
Happy Hacking !!!!!!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
