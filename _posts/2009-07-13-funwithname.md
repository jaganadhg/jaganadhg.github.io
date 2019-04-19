---
layout: post
title: Fun with your name
tags: [Fun, Text Processing, Perl]
use_math: true
comment: true
---
Just I was exploring the [Lingua::EN:: modules](http://search.cpan.org/~yumpy/Lingua-EN-Namegame-0.05/Namegame.pm) in CPAN. I saw a funny module called Lingua::EN::Namegame by 'Tim Maher'. If you give your name as input it will generate some verses. I will tell you how to install and use it. 

Open terminal. Type '`cpan`' as root. Type '`install Lingua::EN::Namegame`' in the cpan terminal . Follow the instructions. If the installation is successful copy and paste the below given code in to your text editor and save it as '`namegame.pl`'. Run it an enjoy.

```perl

#!/usr/bin/env perl
use Lingua::EN::Namegame;

print "Enter your name \n";
$name = <STDIN>;
chomp($name);
$verse = name2verse ($name);

print $verse,"\n";

print "How is it\n";
```

Happy hacking !!!!!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
