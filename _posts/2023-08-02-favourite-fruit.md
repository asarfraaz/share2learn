---
title: "Which is your favourite fruit?"
date: 2023-08-02
author: Sarfraaz Ahmed
category: Tutorial
---

Frequency table mentions the number of occurrences of an item in a container

<p align="center">
<a data-flickr-embed="true" href="https://www.flickr.com/photos/13070711@N03/28416790260/in/photolist-Ki6tHE-EkZNsY-9tfBxK-8kS8jL-NZ2dTF-Yc6zrq-DfsWA9-28VdrAb-oWWmFE-YhjBH7-iv3mzg-27H5Cvv-aCLwJZ-27Va6TC-BHL9Hm-H8cJ5U-25qvVns-2bLtYfz-J5q9EK-24YKX9Y-J7tKnH-26V1iUQ-26EU8gT-283Ndmk-26bK7wT-SsrGXd-c5yyp7-dL8ahQ-H2iV6i-281Yu8H-wrT1fy-23DNBpi-27Zehxm-w8sauF-BUBPV5-HeT2a-dj9xvR-c2d3rW-7wsk9L-U1Jp2e-24T2tc4-5Lpzap-PEoHUm-RFRopU-249q5C8-2wVjWK-9toESf-A7BeNa-25iJQb7-aSmuEp" title="Fruit Shop @ Russell Market" target="_blank"><img src="https://live.staticflickr.com/8158/28416790260_340ece6da1_w.jpg" width="400" height="336" alt="Fruit Shop @ Russell Market"/></a>
<br>
Photo by <a href="https://www.flickr.com/photos/13070711@N03/" target="_blank">P. L. Tandon</a>, some rights reserved
</p>

## Frequency Counter

A Supermarket opened up next to a school. They wanted to conduct a survey to check which fruits children like to eat the most. They go to their school and ask each one to write down their favourite fruit. Let's assume that this is the list that they got by conducting this survey in a classroom of 7 students.

```python
    >>> fruits = [ "apple", "mango", "banana", "apple", "apple", "mango", "grapes" ]
```

We need to create a frequency counter from this list. Or more formally a Frequency table that captures the number of occurrences for each fruit in the list.

You might think that this should do it
```python
    >>> freq = dict()
    >>> for name in fruits:
    ...     freq[name] += 1
    ...
    KeyError : 'apple'
    >>>
```
except that it fails for the very first iteration, since the key `apple` does not exist in the empty (initial) dictionary.

How do you think we can solve this?

## Initialising the Frequency Table

You might suggest to start with a dictionary that contains all the fruit names as its keys with their corresponding values being 0. And then we could write the above code to generate the Frequency Table

```python
    >>> freq = dict()
    >>> # for name in fruits:
    >>> for name in set(fruits): # To reduce the number of iterations
    ...     freq[name] = 0
    ...
    >>> freq
    {'mango': 0, 'banana': 0, 'apple': 0, 'grapes': 0}
```

Now that we have a well initialised dictionary, we can repeat the earlier code and get the Frequency Table

```python
    >>> for name in set(fruits):
    ...     freq[name] += 1
    ...
    >>> freq
    {'apple': 3, 'mango': 2, 'banana': 1, 'grapes': 1}
```

Awesome !! We got the Frequency Table. But, is it worth writing 2 loops for this?

## Useful empty dictionary

The first `for` loop that is used to create a dictionary with values set to 0 can be replaced using `fromkeys()` method of `dict` class. Infact, `fromkeys()` is a classmethod of `dict` class. [ The method name starting with the word "from" itself should be a hint that it is a classmethod ]

Let's check out how `fromkeys` works:

```python
    >>> fruits = [ "apple", "mango", "banana", "apple", "apple", "mango", "grapes" ]
    >>> dict.fromkeys(fruits)
    {'apple': None, 'mango': None, 'banana': None, 'grapes': None}
```

All items in `fruits` list are stored as "keys" in the dictionary. Every key has been assigned a value of `None`. But, we wanted the value to be 0 and not None.

Reading the documentation using [help(dict.fromkeys)](https://docs.python.org/3/library/stdtypes.html#dict.fromkeys){:target="_blank"} we notice that this classmethod takes a "value" parameter that we can specify to be set as the default value instead of `None`

So, let's try setting the default value to 0, that will help solve this problem :

```python
    >>> fruits = [ "apple", "mango", "banana", "apple", "apple", "mango", "grapes" ]
    >>> dict.fromkeys(fruits, 0)
    {'apple': 0, 'mango': 0, 'banana': 0, 'grapes': 0}
```

That works !!!

So, our final code would be

```python
    >>> fruits = [ "apple", "mango", "banana", "apple", "apple", "mango", "grapes" ]
    >>> freq = dict.fromkeys(fruits, 0)
    >>> for name in fruits:
    ...     freq[name] += 1
    ...
    >>> freq
    {'apple': 3, 'mango': 2, 'banana': 1, 'grapes': 1}
```

## Tradeoffs

Some of you might be wondering that we could have easily done this using `defaultdict` class as well. 

```python
    >>> fruits = [ "apple", "mango", "banana", "apple", "apple", "mango", "grapes" ]
    >>> from collections import defaultdict
    >>> freq = defaultdict(int)
    >>> for name in fruits:
    ...     freq[name] += 1
    ...
    >>> freq
    defaultdict(<class 'int'>, {'apple': 3, 'mango': 2, 'banana': 1, 'grapes': 1})
```

The problem with this approach is that we need to import `collections` module. If you plan to use `defaultdict` for more than just this one line of code, or may be use other classes from the wonderful `collections` module, then it makes sense to `import collections` module in your program. But, the solution that we got earlier using `fromkeys` classmethod saves us from such module dependencies.

So, it's a tradeoff between using a module or built-in data structure. For, most of the applications, unless they are Enterprise style programs or Frameworks, using the built-in data structure would be the most preferred option.


## Discussion

[Start a discussion on GitHub](https://github.com/asarfraaz/share2learn/discussions/new/choose){:target="_blank"} about this article and let me know your thoughts or suggestions.


