---
layout: post
title: POS Tagging with Perl
tags: [Natural Language Processing, POS Tagging, Perl, NLPROC]
use_math: true
---
POS Tagging (Parts of Speech Tagging ) is the process of assigning correct Parts of Speech Tag to words in a text. You can find a more elaborated definition from the wiki article ["Part-of-speech tagging"](http://en.wikipedia.org/wiki/Part-of-speech_tagging). 

So many POS Taggers are available for English under GPL and other licences. Some of the famous taggers are 'Stanford POS Tagger', Brill POS Tagger', 'Genia Tagger' etc... Have a look on the Stanford NLP repository link.

Here in this post I would like to show how POS Tagging can be done with a simple Perl script. 

There is Pertl module available in the [CPAN site](http://search.cpan.org/) called [Lingua::EN::Tagger](http://search.cpan.org/~acoburn/Lingua-EN-Tagger-0.15/Tagger.pm) . It is a tagger module for English and some other Europian Languages. Let us see how it can be used for POS Tagging.

Installing Lingua::EN::Tagger in GNU/Linux

Open Terminal. Run cpan as root. Type `install Lingua::EN::Tagger` enter(Assumes that you are connected to Internet). Follow the instructions. Make sure that tagger is installed. Exit CPAN.

Using `Lingua::EN::Tagger`

Now open your favourite editor (I prefer VIM). Copy and paste/type the below given code and save it in to a file called 'tager.pl'. Run 'perl tager.pl your_text_file .
 
```perl
#!/usr/bin/env perl
use Lingua::EN::Tagger qw(add_tags);
my $postagger = new Lingua::EN::Tagger;

while (<>) {
    chomp $_;
    my $text = $_;

    my $tagged = $postagger->add_tags($text);

    print $tagged, "\n";
}
```


Code Explanation
```perl
use Lingua::EN::Tagger qw(add_tags);
````
Imports `Lingua::EN::Tagger`

```perl 
my $postagger = new Lingua::EN::Tagger;
```

Creates object of the tgger.
Then it reads a text file given as argument and performs the tagging.
Happy Hacking!!!!!


Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
