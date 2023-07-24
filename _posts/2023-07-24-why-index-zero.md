---
title: "Why should index start from 0?"
date: 2023-07-24
author: Sarfraaz Ahmed
category: TIL
---

<p align="center">
<a data-flickr-embed="true" data-header="true" data-footer="true" href="https://www.flickr.com/photos/s_raaz/313020754/" title="Bangalore Winter"><img src="https://live.staticflickr.com/119/313020754_e369b25de7_w.jpg" width="400" height="300" alt="Bangalore Winter"/></a>
<br>
Photo by <a href="https://www.flickr.com/photos/s_raaz/313020754/">Sarfraaz Ahmed</a>, all rights reserved
</p>

- When you count the number of chairs in a room, you start counting from 1
- When you count the number of people ahead of you in a queue, you start counting from 1

Almost all things we count in real life, we start counting from 1. Then why do we start indexing from 0 and not 1 ?

The simple answer to this is : Is looks nice :-) ( As mentioned by Edsger W. Dijkstra ) Yes, he is the same person who came up with the solution for the very famous travelling salesman problem. The algorithm is appropriately called “Dijkstra’s algorithm”. Read and be amused to find out how he came up with this solution in 20 minutes !!! ( read more here[https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm#History] )

The long answer is that has been carried forward all the way from great old days of Hardware referencing ( and so in Assemble code as well ) : http://python-history.blogspot.com/2013/10/why-python-uses-0-based-indexing.html?showComment=1456103041409#c4251845305075300023

The C language has its own reasons for indexing from zero. The obvious reason is that an array variable is also a pointer to the first element of the array. And so, its index is zero, since you then want to be able to access ’n’th element in the array using (arr + n). For the first element, it would work elegantly only if ’n’ starts from 0. This answer on StackOverflow gives you a technically more detailed explanation : https://stackoverflow.com/a/13519429/410645

When it comes to Python, indexing from 0 makes perfect sense when we think of slicing. Using the slicing syntax, if we want to fetch the first 3 elements, we would say ex[:3]. If the indexing would have started from 1, to fetch the first 3 elements, we would have to use something ugly like ex[1:4]. Guido speaks about similar reasoning on why he decided to go with 0 indexing here : http://python-history.blogspot.com/2013/10/why-python-uses-0-based-indexing.html

Coming back to why Djikstra called it “nice”. You can read his hand written manuscript at :  https://www.cs.utexas.edu/users/EWD/ewd08xx/EWD831.PDF Or a more formal html document at : https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html Explains the mathematical reasoning behind it. Though, the problem he is tackling in mathematics is not exactly same as that in Computer Science. But, the thought process seems to be the same. A very well made video on this same article with some colourful visuals is available at : https://www.youtube.com/watch?v=saZnPDPyQHA

On a side note, if you would like to know more about Djikstra, you can find more information at : https://www.cs.utexas.edu/users/EWD/welcome.html

Shows how much he cared for his students : https://www.cs.utexas.edu/users/EWD/OtherDocs/To%20the%20Budget%20Council%20concerning%20Haskell.pdf

