---
layout: post
title: Generating pronunciation of English words with Perl.
tags: [Text Processing, Natural Language Processing, Perl]
use_math: true
comment: true
---
Today we can discuss a Perl module called [Lingua::EN::Phoneme](http://search.cpan.org/~marnanel/Lingua-EN-Phoneme-0.01/lib/Lingua/EN/Phoneme.pm). This module is used for generating pronunciation of words in a given English text. The lexicon which is used in the module is [CMU Pronunciation lexicon](http://www.speech.cs.cmu.edu/cgi-bin/cmudict).  CMU have an Open Source Speech Recognition tool called ['Sphinx'](http://www.speech.cs.cmu.edu/). Sphinx based Speech Recognition work for Indian languages is in progress. Some individuals, groups and organisations are engaged in this. Here we are not going to discuss about Speech Recognition.  

The module Lingua::EN::Phoneme converts a given word to its pronunciation representation in ARPABET, e.g testing => TEH1STIH0NG. If you give your name as input it may not work! Because your name may not be present in the CMU pronunciation dictionary.  

Let us see how to install it.

Open terminal. Invoke the 'cpan' terminal as root user. Type 'install Lingua::EN::Phoneme'. Follow the instructions. 

For testing it a sample code is given in the CPAN site. I am just copying it here. I will explain how to use it in a raw text file too. 

The code for test run of the module.

```perl
#!/usr/bin/env perl

use Lingua::EN::Phoneme;
my $lep = new Lingua::EN::Phoneme();
for ($lep->phoneme('cakes')) { print "$_ is a phoneme"; }
```

Copy and paste the code to your favourite editor and save it as 'phoneme.pl'. Run it ie 'perl phoneme.pl'. If you are getting a message like this "K is a phonemeEY1 is a phonemeK is a phonemeS is a phoneme", your module is working in your system.

Let us see how it can be applied over a raw English text file. I am giving another piece of code below.

```perl
#!/usr/bin/env perl
use Lingua::EN::Phoneme;
my $cmu = new Lingua::EN::Phoneme;
open( TEF, "<$ARGV[0]" ) or "Failed open the file \n";
$text = <TEF>;
#Opens file and stores the content to $text
$text =~ s/ +/ /g;
$text =~ s/\n/ /g;
@words = split( /\s/, $text );
# Replaces morethan one space with single space and splits in to words
for ( $p = 0 ; $p <= $#words ; $p++ ) {
    $words[$p] =~ s/\.//g;
    $words[$p] =~ s/\,//g;
    #Replaces full stop and comma. IF it is attached to word lexical lookup will fail
    print $words[$p], "\t\t", $cmu->phoneme( $words[$p] ), "\n";
    #Prints the word and its pronounciation

}
```

Copy and paste this code to your favourite browser and save it as 'phone.pl'. Also you crate a flat file with some English sentences. Run the script as 'perl phone.pl <your_word_list>'. Now you will get pronunciation of each and every word in the file.  One thing you have to remember, for all most all Indian names it may not be giving a result.

To get a clear understanding of the output you have to look in to the [ARPABET schema](http://en.wikipedia.org/wiki/Arpabet). Some numerals '0','1' and '2' will be appearing in the output. '0' indicates no primery stress, '1' indicates primary stress and '2' indicates secondery stress(Applicable to vowels).

Another matter (I think it is my mistake). When you are running the second code it may throw an error message "Use of uninitialized value in split at /usr/local/share/perl/5.10.0/Lingua/EN/Phoneme.pm line 31, <TEF> line 1.". I am trying to resolve it!. One thing if you collect the output to a file the error message will not appear. 

If pronunciation lexicon for Indian languages comes under GPL then some one can write Lingua::IN::Phoneme too!! :-) 

Happy Hacking!!!!!



Migrated from my [old blog jaganadhg.freeflux.net](https://web.archive.org/web/20160323193721/http://jaganadhg.freeflux.net/blog)
