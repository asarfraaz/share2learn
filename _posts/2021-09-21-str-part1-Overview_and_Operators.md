---
title: "Python Strings : Part1 - Overview and String Operators"
date: 2021-09-21
author: Nagarjun V
category: Tutorial
---
<br>

!!! Hi There ! Welcome to share2learn !!! 

This blog is all about to have fun with String,Text processing in python

Lets divide this String tutorial into 3 parts

<br>

**Part 1 - Strings Overview & String Operators**

**Part 2 - String Formatting**

**Part 3 - Strings methods**

<br>

This Blog covers **Part 1** and will continue other parts in upcoming blogs

ok, enough talking, lets move on ,

<br>

<H2> What is String in Python</H2>

String is an immutable sequence data type

It is the sequence of Unicode characters wrapped inside single, double, or triple quotes.

**example:**

```python
'HI there I am STRING in Python with single quotes'

"HI there I am STRING in Python with double quotes" 

'''HI there I am STRING in Python with triple quotes'''

"""HI there I am STRING in Python with triple double-quotes"""
```
**Q:** if we want to perform some basic operations on Strings in python, how can we do it ?

**ANS:** we have multiple options , operators are one of them .Lets look at available String operators in python

<H3>String Operators</H3>

"+" - Concatenation
```python
>>> "Hello" + 'Python'
'HelloPython'
```

"*" - Repetition
```python
>>> "hello"*5
'hellohellohellohellohello'
```

[] - Slice
```python
>>> text = "Hello Python"
>>> text
'Hello Python'
>>> text[0]
'H'
>>> text[-1] # accessing last element using negative indexing
'n'
```

[ : ] -  Slice in Range
```python
>>> text[0:5]
'Hello'
>>> text[:5] #from starting index upto 4
'Hello'
>>> text[2:5] #from index 2 to 4
'llo'
>>> text[1::] #from index 1 to last
'ello Python'
>>> text[::-1] #From last index to first, from right to left
'nohtyP olleH'
```

in |  not in - Membership 
```python
#**in** returns True if if match exists
>>> text
'Hello Python'
>>> "Hello" in text
True
>>> "hello" in text
False

#**in** returns True if if match NOT exists
>>> "hello" not in text
True
>>> "Hello" not in text
False
```

r/R - Raw String
```python
#Suppresses actual meaning of Escape characters
>>> print (r'\n')
\n
>>> print (R'\n')
\n

```

% - Format
Performs String formatting. Let us see Formatting in details with Part-2



