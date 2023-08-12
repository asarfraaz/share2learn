---
title: "Swapping dictionary keys and values"
date: 2023-08-12
author: Sarfraaz Ahmed
category: Tutorial
---

The ranks secured by students in class can be represented in a Python dictionary as shown below
```python
    >>> rank = {
                'Sachin' : 1,
                'Sehwag' : 2,
                'Dhoni'  : 3,
                'Virat'  : 3,
                'Rohit'  : 4,
                'Manoj'  : 5,
```

<p align="center">
<a data-flickr-embed="true" href="https://www.flickr.com/photos/13070711@N03/28416790260/in/photolist-Ki6tHE-EkZNsY-9tfBxK-8kS8jL-NZ2dTF-Yc6zrq-DfsWA9-28VdrAb-oWWmFE-YhjBH7-iv3mzg-27H5Cvv-aCLwJZ-27Va6TC-BHL9Hm-H8cJ5U-25qvVns-2bLtYfz-J5q9EK-24YKX9Y-J7tKnH-26V1iUQ-26EU8gT-283Ndmk-26bK7wT-SsrGXd-c5yyp7-dL8ahQ-H2iV6i-281Yu8H-wrT1fy-23DNBpi-27Zehxm-w8sauF-BUBPV5-HeT2a-dj9xvR-c2d3rW-7wsk9L-U1Jp2e-24T2tc4-5Lpzap-PEoHUm-RFRopU-249q5C8-2wVjWK-9toESf-A7BeNa-25iJQb7-aSmuEp" title="Fruit Shop @ Russell Market" target="_blank"><img src="https://live.staticflickr.com/8158/28416790260_340ece6da1_w.jpg" width="400" height="336" alt="Fruit Shop @ Russell Market"/></a>
<br>
Photo by <a href="https://www.flickr.com/photos/13070711@N03/" target="_blank">P. L. Tandon</a>, some rights reserved
</p>

## Working with Dictionary data

Using the `rank` dictionary it is now very easy to find the rank of a student . To find `Dhoni`'s rank, we can do something like

```python
    >>> rank['Dhoni']
    3
    >>> rank.get('Dhoni')
    3
```

The `get()` method comes in handy when dealing with names that might not be present in the dictionary

```python
    >>> rank['Dravid']
    KeyError: ...
    >>> rank.get('Dravid', 'N/A')
    'N/A'
    >>> rank.get('Dhoni', 'N/A')
    3
```

## Swapping key-value pairs

How can we find the name of the student who secured 2nd rank using the `rank` dictionary ?

To be able to answer that question, it would be more useful to have a dictionary that stored the ranks of students as keys and their names as values

Let's swap the key-value pairs of `rank` dictionary using a simple Dictionary Comprehension

```python
    >>> names = { val:key for key,val in rank.items() }
    >>> names[1]
    'Sachin'
    >>> names
    { 1: 'Sachin', 2: 'Sehwag', 3: 'Virat', 4: 'Rohit', 5: 'Manoj' }
```

Something looks fishy in that new `names` dictionary created above. Dhoni's name is missing !! Where did that go ?


## Discussion

[Start a discussion on GitHub](https://github.com/asarfraaz/share2learn/discussions/new/choose){:target="_blank"} about this article and let me know your thoughts or suggestions.


