---
title: "Swapping dictionary keys and values"
date: 2023-08-12
author: Sarfraaz Ahmed
category: Tutorial
---

Schools were (and some are still) notorious for building a sense of competition in children through their "ranking" system. The one who writes the most number of correct answers ( irrespective of how much that student understood it ) always gets a better rank than someone who just could not put the answer in the right words ( as expected by the evaluator )

However one may feel about that "ranking" system, it comes in handy while learning something about Python Dictionaries.

<p align="center">
<a data-flickr-embed="true" href="https://www.flickr.com/photos/nadircruise/6425616037/in/photolist-4wkEdj-Fg6Sen-2aJykpK-Nn9a1T-2b2maas-2aJymk2-2b2m9pj-2b2maNb-Nn96BP-2b2mbMW-aNBFBM-29mQf3L-29mQcZs-2c3SC6f-2b2mbk3-Nn99j2-2c8majP-2aJygHB-Wfik9f-2aJyf94-aMP2Hx-aMNTzF-aMNSRi-aMNXMp-aMNSce-aMNZMD-aMNUGa-JE5Q5x-27dzrrA" title="Battle Royale" target="_blank"><img src="https://live.staticflickr.com/6100/6425616037_1472443038_w.jpg" width="400" height="267" alt="Battle Royale"/></a>
<br>
Photo by <a href="https://www.flickr.com/photos/nadircruise/" target="_blank">Nadir Hashmi</a>, some rights reserved
</p>

The ranks secured by students in a class can be represented in a Python Dictionary as shown below
```python
    >>> toprank = {
                    'Sachin' : 1,
                    'Sehwag' : 2,
                    'Dhoni'  : 3,
                    'Virat'  : 3,
                    'Rohit'  : 4,
                    'Manoj'  : 5,
                   }
```


## Working with Dictionary data

Using the `toprank` dictionary it is now very easy to find the rank of a student . To find `Dhoni`'s rank, we can do something like

```python
    >>> toprank['Dhoni']
    3
    >>> toprank.get('Dhoni')
    3
```

The `get()` method comes in handy when dealing with names that might not be present in the dictionary

```python
    >>> toprank['Ganguly']
    KeyError: ...
    >>> toprank.get('Ganguly')
    >>>
    >>> toprank.get('Ganguly', 'N/A')
    'N/A'
    >>> toprank.get('Dhoni', 'N/A')
    3
```

So, how can we find the name of the student who secured 2nd rank using the `toprank` dictionary ?


## Swapping key-value pairs

To be able to answer that question, it would be more useful to have a dictionary that stored the ranks of students as keys and their names as values

Let's swap the key-value pairs of `toprank` dictionary using a simple Dictionary Comprehension

```python
    >>> names = { val:key for key,val in toprank.items() }
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

Well, on a closer look at the original `toprank` dictionary you will notice that "Dhoni" and "Virat" secured the same ranks.
- When the `names` dictionary was populated for the rank "3", it first added "Dhoni" as its value.
- Then, when it picked the next element from `toprank`, it noticed the key "3" already being present in `names` dictionary.
- Since keys are unique in a dictionary, no new key-value pair was created.
- Rather, it updated the value corresponding to the existing key "3"
- For the existing key "3", the new value "Virat" replaced the existing value "Dhoni".

So, that is why "Virat" replaced "Dhoni" :-)

A proper way of storing this information about more than one person having secured the same rank, can be achieved if we store all the names as a list for the given rank

## Dictionary of keys with a list of values

To create a dictionary of list, we would have to first initialise the dictionary, such that every key is created with an empty list. We can then iterate over each "rank" and simply append the person's "name" to that existing list.

Let's use the [technique we saw in our previous post](https://asarfraaz.github.io/share2learn/tutorial/2023/08/02/favourite-fruit.html), and use `dict.fromkeys()` classmethod to initialise the dictionary. We need to be careful to use the values of `toprank` dictionary for creating the keys of the new `names` dictionary

```python
    >>> names = dict.fromkeys(toprank.values(), [])
    >>> names
    {1: [], 2: [], 3: [], 4: [], 5: []}
    >>>
```

We now need to iterate over `toprank` dictionary and append the student's name to `names` dictionary

```python
    >>> for stu in toprank:
    ...     new_key = toprank[stu]
    ...     new_val = stu
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

Oops!! That does not look good. What just happened there?

This is a typical side effect of using an empty list as an initial value. Python creates the default empty list at compile time, and so every key gets a reference to the same original empty list. We can verify that by checking the ids of the lists

```python
    >>> for key in names:
    ...     print(id(names[key]))
    ...
    4335532544
    4335532544
    4335532544
    4335532544
    4335532544
    >>>

    >>> # Or just trying to be more adventurous to get a more meaningful output
    >>> for key in names:
    ...     idstr = f'id(names[{key!r}])'
    ...     print(f'{idstr} = {eval(idstr)}')
    ...
    id(names[1]) = 4335532544
    id(names[2]) = 4335532544
    id(names[3]) = 4335532544
    id(names[4]) = 4335532544
    id(names[5]) = 4335532544
    >>>
```

So, what we need is a way to create a new list everytime a new key is added to `names` dictionary. We want the key to be given a "default" value of `[]` everytime it is created for the first time. This is exactly what `dict.setdefault` does !!!


## Using setdefault method

`setdefault` method of dictionary is a complement of the `get` method, but useful when you want to set a value to a key for the first time we seek it. It automatically detects the absence of the key and creates it for us. It also assigns the default value at the time of creating this new key in the dictionary. The following example might make it easy to understand how it works

```python
    >>> fun = dict()
    >>> fun
    {}
    >>> fun.get(10)
    >>> fun.setdefault(10, [])
    []
    >>> fun
    {10: []}
```

Notice that the `setdefault` method does 2 things

- It first creates the new key-value pair, assigning the default value `[]` to the new key
- And it also returns the new value : `[]`

We can use the returned value to perform some operations on it.

```python
    >>> fun = dict()
    >>> retval = fun.setdefault(10, [])
    >>> fun
    {10: []}
    >>> retval
    []
    >>> retval.append("abcd")
    >>> retval
    ['abcd']
    >>> fun
    {10: ['abcd']}
```

The best part is that it now returns the existing list for subsequent calls of setdefault for an existing key. So, we can easily chain `setdefault` with `append` to add a new value to the newly created list

```python
    >>> fun.setdefault(10, [])
    ['abcd']
    >>> 
    >>> fun.setdefault(20, []).append("xyz")
    >>> # append does not return any value
    >>> fun
    {10: ['abcd'], 20: ['xyz']}
    >>>
```

## Final Solution

Let's combine all the things we learnt above to solve the problem at hand

```python
    >>> toprank 
    {'Sachin' : 1, 'Sehwag' : 2, 'Dhoni'  : 3, 'Virat'  : 3, 'Rohit'  : 4, 'Manoj'  : 5}
    >>>
    >>> names = dict()
    >>> for stu in toprank:
    ...     new_key = toprank[stu]
    ...     new_val = stu
    ...     names.setdefault(new_key, []).append(new_val)
    ...
    >>>
    >>> names
    {1: ['Sachin'], 2: ['Sehwag'], 3: ['Dhoni', 'Virat'], 4: ['Rohit'], 5: ['Manoj']}
    >>>
    >>> names[3]
    ['Dhoni', 'Virat']
    >>>
```

## Tradeoffs

The tradeoffs of using this approach to using `defaultdict` with `[]` from `collections` module are exactly same as we saw in "[Favourite Fruit](https://asarfraaz.github.io/share2learn/tutorial/2023/08/02/favourite-fruit.html)" post


## Discussion

[Start a discussion on GitHub](https://github.com/asarfraaz/share2learn/discussions/new/choose){:target="_blank"} about this article and let me know your thoughts or suggestions.


