---
title: "Swapping dictionary keys and values"
date: 2023-08-12
author: Sarfraaz Ahmed
category: Tutorial
---

Schools were (and some are still) notorious for building a sense of competition in children through their "ranking" system. The one who writes the most number of correct answers ( irrespective of how much that student understood it ) always gets a better rank than someone who just could not put the answer in the right words ( as expected by the evaluator )

However one may feel about that "ranking" system, it comes in handy while learning something about Python Dictionaries. The ranks secured by students in class can be represented in a Python Dictionary as shown below
```python
    >>> ranks = {
                'Sachin' : 1,
                'Sehwag' : 2,
                'Dhoni'  : 3,
                'Virat'  : 3,
                'Rohit'  : 4,
                'Manoj'  : 5,
               }
```

<p align="center">
<a data-flickr-embed="true" href="https://www.flickr.com/photos/47134714@N04/48144513087/in/photolist-2gmndpR-GZbdUh-23rfC7K-dPEpSs-78NL36-2o8HPe8-Cd4dnS-Cez8M2-dKJ87N-BUJncU-Fpfa2k-M9vHGT-2mwPnw4-BP7UYa-rsJzdF-2mx12ab-EzWcxy-FxuUwW-EAcddF-2mwNnb5-2mwNnfo-CmS3Ba-L7ktcs-BNmgoZ-2omcZFY-Qb7RLp-Akm6Nh-RNrvNC-2nCYfYf-CoMrXx-2mwJBuA-2mwPnoU-2mx2gdM-2dRNVad-Ftzs4j-FphRAT-Vz3doJ-2oDoCgj-CUYopT-2cQqj1W-2g6CcL6-24oJebW-2cxDGzR-2mzErhx-2dRNWJW-2mwKSVv-2jLX5TH-2jZkfAC-EMgiyg-EMgig2" title="Mirror Mirror on the Wall...." target="_blank"><img src="https://live.staticflickr.com/65535/48144513087_5bd619f61f_w.jpg" width="400" height="191" alt="Mirror Mirror on the Wall...."/></a>
<br>
Photo by <a href="https://www.flickr.com/photos/47134714@N04/" target="_blank">Ed</a>, some rights reserved
</p>

## Working with Dictionary data

Using the `ranks` dictionary it is now very easy to find the rank of a student . To find `Dhoni`'s rank, we can do something like

```python
    >>> ranks['Dhoni']
    3
    >>> ranks.get('Dhoni')
    3
```

The `get()` method comes in handy when dealing with names that might not be present in the dictionary

```python
    >>> ranks['Dravid']
    KeyError: ...
    >>> ranks.get('Dravid', 'N/A')
    'N/A'
    >>> ranks.get('Dhoni', 'N/A')
    3
```

## Swapping key-value pairs

How can we find the name of the student who secured 2nd rank using the `ranks` dictionary ?

To be able to answer that question, it would be more useful to have a dictionary that stored the ranks of students as keys and their names as values

Let's swap the key-value pairs of `ranks` dictionary using a simple Dictionary Comprehension

```python
    >>> names = { val:key for key,val in ranks.items() }
    >>> names[1]
    'Sachin'
    >>> names
    { 1: 'Sachin', 2: 'Sehwag', 3: 'Virat', 4: 'Rohit', 5: 'Manoj' }
```

And we can now access rank holder names based on their ranks as below:

```python
    >>> names[3]
    'Virat'
    >>> names.get(3, None)
    'Virat'
```

Oops !!! We expected "Dhoni", but got "Virat". What's going wrong here ? Something looks fishy in that new `names` dictionary created above. Doesn't it? Dhoni's name is missing !! Where did that go ?

Well, on closer look at the original `ranks` dictionary you will notice that "Dhoni" and "Virat" secured the same ranks. When the `names` dictionary for populated, for the rank "3", it first added "Dhoni" as its value. Then, when it picked the next element from `ranks`, it noticed the key "3" already being present in `names` dictionary. Since keys are unique in a dictionary, the new value "Virat" replaced the existing value "Dhoni". So, that is why "Virat" replaced "Dhoni" :-)

A proper way of storing this information about more than one person have secured the same rank, can be achieved if we store all the names as a list for the given rank

## Dictionary of keys with a list of values

To create a dictionary of list, we would have to first initialise the dictionary, such that every key is created with an empty list. We can then iterate over each "rank" and simply append the person's "name" to that existing list. We need to make sure that the values of `ranks` dictionary should be used to create the keys of `names` dictionary

Let's use the technique we saw in our previous post, and use `dict.fromkeys()` classmethod to initialise the dictionary

```python
    >>> names = dict._fromkeys(ranks.values(), [])
    >>> names
    {1: [], 2: [], 3: [], 4: [], 5: []}
```

We now need to iterate over `ranks` dictionary and append the name to `names` dictionary

```python
    >>> for name in ranks:
    ...     new_key = ranks[name]
    ...     new_val = name
    ...     names[new_key].append(new_val)
    ...
    >>> from pprint import pprint
    >>> pprint(names)
    {1: ['Sachin', 'Sehwag', 'Dhoni', 'Virat', 'Rohit', 'Manoj'],
     2: ['Sachin', 'Sehwag', 'Dhoni', 'Virat', 'Rohit', 'Manoj'],
     3: ['Sachin', 'Sehwag', 'Dhoni', 'Virat', 'Rohit', 'Manoj'],
     4: ['Sachin', 'Sehwag', 'Dhoni', 'Virat', 'Rohit', 'Manoj'],
     5: ['Sachin', 'Sehwag', 'Dhoni', 'Virat', 'Rohit', 'Manoj']}
    >>>
```


## Discussion

[Start a discussion on GitHub](https://github.com/asarfraaz/share2learn/discussions/new/choose){:target="_blank"} about this article and let me know your thoughts or suggestions.


