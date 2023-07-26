---
title: "Why should index start from 0?"
date: 2023-07-24
author: Sarfraaz Ahmed
category: TIL
---

- When you count the number of chairs in a room, you start counting from 1
- When you count the number of people ahead of you in a queue, you start counting from 1

Almost all things we count in real life, we start counting from 1. Then why do we start indexing from 0 and not 1 ?

<p align="center">
<a data-flickr-embed="true" href="https://www.flickr.com/photos/albedo20/26556937242/in/photolist-GsKfdj-nWd6jA-djb1hA-JggB9o-bu8PG7-g21ZiK-bof4L9-r2gXkN-25HeCA1-oK9ACu-9Jhdtf-4uEftT-FdZmPu-F3jXzx-nATWEB-R5C3s3-aq5Fem-s9UWgQ-4R9Vj7-x2aK3L-aVTcJM-r7Ue5y-CBDAcX-xQBkX-GmpSyb-i8kTF-V7QCU7-MZiCHM-ro1YTv-pw3VBc-7U4y9t-bfvTVV-oP9kaj-2auZgWX-rT6iNb-FxW2oN-SSwygX-252RB2r-7uzZCi-bH3Bmt-bBifSU-oCjCry-pt1Jry-JVyJd9-a5Kx3g-aE2uJS-NcdtFk-wiz6gN-K23dBr-kfLEgt" title="Electric vehicle parking at Google" target="_blank"><img src="https://live.staticflickr.com/1671/26556937242_9c02d76288_w.jpg" width="400" height="300" alt="Electric vehicle parking at Google"/></a>
<br>
Photo by <a href="https://www.flickr.com/photos/albedo20/" target="_blank">albedo</a>, some rights reserved
</p>

## Simple answer

The simple answer to this question is : 

```It looks nice```  😄
( As mentioned by [Edsger W. Dijkstra](https://www.cs.utexas.edu/users/EWD/welcome.html){:target="_blank"} )

Yes, he is the same Dijkstra who came up with the solution for the very famous travelling salesman problem, called “Dijkstra’s algorithm” that forms the foundation for the algorithms that you use on "Google Maps" and similar route based mobile Apps.

On a side-note, it was fun to read how he got the solution for this problem in just 20 minutes !!!

```
    One morning I was shopping in Amsterdam with my young fiancée, and 
    tired, we sat down on the café terrace to drink a cup of coffee and 
    I was just thinking about whether I could do this, and I then 
    designed the algorithm for the shortest path. As I said, it was 
    a twenty-minute invention. 
```

_-- Excerpts from [Wikipedia](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm#History){:target="_blank"}_

So, next time, when your fiancée calls you for shopping, you know what to do :D

## The Python language reasoning

Interestingly enough, the reason for using a particular number for the first index is not the same for all languages. Infact, there are other languages, most notably like Matlab, that don't even use 0 for the first index. They use 1 to denote the first index and not 0.

When it comes to Python, indexing starts from 0. This makes perfect sense when we think of slicing. Using the slicing syntax, 

if we want to fetch the first 3 elements, we would say 

```ex[:3]``` 

If the indexing would have started from 1, to fetch the first 3 elements, 
we would have to use something ugly like 

```ex[1:4]```

or

```ex[:4]``` 

Guido too speaks of a similar reasoning [in his blog](http://python-history.blogspot.com/2013/10/why-python-uses-0-based-indexing.html){:target="_blank"} about why he decided to go with 0 indexing

## The C language reasoning

The C language has its own reasons for indexing from zero. In C, an array variable is also a pointer to the first element of the array. And so, when you want to access the 'n'th element in the array ```a``` using ```a[n]``` it internally gets converted to ```(a + n)```

For the first element, the above logic would work elegantly, only if 'n' starts from 0

[This answer on StackOverflow](https://stackoverflow.com/a/13519429/410645){:target="_blank"} gives you a technically more detailed explanation


## The Assembly code reasoning

[This comment on Guido's blog post](http://python-history.blogspot.com/2013/10/why-python-uses-0-based-indexing.html?showComment=1456103041409#c4251845305075300023){:target="_blank"} takes the discussion even further down to the hardware level. This implies that it was such a natural thing to do in the Assembly code

The explanation is pretty straight forward to understand. If we have to represent first 8 numbers in binary numbering system, we would choose binary numbers from 000 to 111 ( 0 to 7 ). Numbering starts from 0 !!! And we can do this using 3 bits.

If on the contrary, we had chosen to represent first 8 numbers as 1 to 8 in binary, then we would represent them in binary numbering system from 0001 to 1000 using 4 bits

So, in simple terms, starting from 0 saves us one extra bit.


## The Mathematical reasoning

Coming back to why Djikstra called it “nice”. You can read his [hand written manuscript](https://www.cs.utexas.edu/users/EWD/ewd08xx/EWD831.PDF){:target="_blank"} maintained by his colleagues in The University of Texas at Austin. It explains the mathematical reasoning behind choosing a zero index for mathematical operations. Mind you, this is not the same problem we have been discussing in Computer Science. But, it sort of alludes to the same reasoning.


You might also want to checkout a [very well made video](https://www.youtube.com/watch?v=saZnPDPyQHA){:target="_blank"} on this same article with some colourful visuals


In Mathematical terms, there are 2 problems that are being discussed. First is to figure out the numbers to denote a range of numbers. Should we include the start and end numbers or not ? If I want to represent numbers from 11, 12, 13, 14 then should I represent them as 

```numbers between 11 and 14``` or 

```numbers between 11 and 15``` or 

```numbers between 10 and 14``` or 

```numbers between 10 and 15``` ?

And then once we have chosen the best option among the 4 options mentioned above, we now need to figure out if the first number should be indexed at 0 or 1


You can read the arguments in a more [formal html document](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html){:target="_blank"}.   


On a side note, this [letter by Djikstra on why students should be introduced to programming using Haskell instead of Java](https://www.cs.utexas.edu/users/EWD/OtherDocs/To%20the%20Budget%20Council%20concerning%20Haskell.pdf){:target="_blank"} shows how much he cared for his students

