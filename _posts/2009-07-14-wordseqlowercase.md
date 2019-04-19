---
layout: post
title: Converting word sequence to title case in Perl and Python.
tags: [Text Processing, Python, Perl, Natural Language Processing]
use_math: true
comment: true
---
People working in Natural Language Processing often extract mutiword units. Some multiword units may be names of Organisation or departments like. Some times they may require to convert it to exact title case(department of physics to Department of Physics ). There is a perl module for performing this operation called [Lingua::EN::Titlecase](http://search.cpan.org/~ashley/Lingua-EN-Titlecase-0.14/lib/Lingua/EN/Titlecase.pm) . If you are a Pythonist (me tooo) you may tell that it is easy in Python. Because there is a function called title() in Python. But this perl module is more intelligent than  the title() in Python. The out put of title() function in Python is like this.

```python
$ python
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> x = "department of physics"
>>> x.title()
'Department Of Physics'
>>> 
```

See the perl output :

```
~/perl$ perl ftit.pl p
```

Department of Physics

I think now you got why I am telling that the perl module is more intelligent that Pthon title().

Let us stop debating. First install the module `Lingua::EN::Titlecase` in your system.
To install the module in GNU/Linux system follow the below given steps.
Open terminal. Type '`cpan`' as root user. Type '`install Lingua::EN::Titlecase`' and follow the instructions.
Then copy the below given code to your favourite editor and save it as '`title.pl`'. Now prepare a list of word like 'department of physics'. Now run the script. To run the script open terminal and go the directory where the 'title.pl' is located. Run '`perl title.pl <your_list>`.
 

```perl

#!/usr/bin/env perl
use Lingua::EN::Titlecase;
my $tle_case = new Lingua::EN::Titlecase;

open( TCF, "<$ARGV[0]" ) or die "Failed to open\n";

while (<TCF>) {
    my ($totc) = $_;
    print $tle_case->title($totc);

}


```

As I mentioned earlier the same can be done in python with out any external module. 
Copy and paste the below given code to your favourite editor and save as 'tc.py'. Run 'python tc.py <your_wordlist>. The result will be slightly different from the perl code. Spot it out.

```python
#!/usr/bin/env python
import sys

def con2Title(words):
        word_list = open(words,'r').readlines()
        for w in word_list:
                print w.title()


word = sys.argv[1]

con2Title(word)

```


Happy hacking!!!!!!!!!!1


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
