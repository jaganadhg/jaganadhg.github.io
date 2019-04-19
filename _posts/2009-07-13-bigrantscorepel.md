---
layout: post
title: Finding Bigrams with t-score in Perl
tags: [Text Processing, Natural Language Processing]
use_math: true
comment: true
---
In this post I will tell how we can find bigrams with tscore from an English text. If you are interested to read more on Bigram see the wiki article at [http://en.wikipedia.org/wiki/Bigram](http://en.wikipedia.org/wiki/Bigram). 

There is a module called [Lingua::EN::Bigram](http://search.cpan.org/~emorgan/Lingua-EN-Bigram-0.01/lib/Lingua/EN/Bigram.pm) in the [CPAN](http://search.cpan.org/) directory. I know that if you are a Perl NLP man you might have created your own perl code for doing the same. Let it be there. We can see how it can be made possible with the above said module. 

To install the module run 'cpan' as root(Assumes that you are connected to Internet). Type 'install Lingua::EN::Bigram' in the cpan terminal and follow the instructions. If the installation is ok then copy and paste below given code to your favourite editor and save it as 'bigram.pl' . 

```perl

#!/usr/bin/env perl
use Lingua::EN::Bigram;

$bigram = new Lingua::EN::Bigram;

while (<>) {
    $text = $_;
    $text =~ tr/A-Z/a-z/;
    $text =~ s/\.//g;
    $text =~ s/\,//g;
    $text =~ s/\?//g;
    $text =~ s/\!//g;
    $text =~ s/\://g;
    $text =~ s/\;//g;
    $bigram->text($text);
    $tscore = $bigram->tscore;
    foreach ( sort { $$tscore{$b} <=> $$tscore{$a} } keys %$tscore ) {
        print "$$tscore{$_} \t " . "$_\n";
    }
}


```


To run the program, open terminal and go to the directory where the `bigram.pl` is located. Type `perl bigram.pl <your_textfile>` .



Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
