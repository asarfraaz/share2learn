---
Title: "Python Strings : Part1 - Overview and String Operators"
Date: 2021-09-21
Author: Nagarjun V
Category: Tutorial
---



Hi There ! Welcome to share2learn !!! 

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

**What is String in Python**

String is an immutable sequence data type

It is the sequence of Unicode characters wrapped inside single, double, or triple quotes.

**example: **

```python
'HI there I am STRING in Python with single quotes'

"HI there I am STRING in Python with double quotes" 

'''HI there I am STRING in Python with triple quotes'''

"""HI there I am STRING in Python with triple double-quotes"""
```

**String Operators**

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
>>> text[:5]
'Hello'
>>> text[2:5]
'llo'
>>> text[1::]
'ello Python'
>>> text[::-1]# String reverse
'nohtyP olleH'
```

in |  not in - Membership 
```python

```

r/R - Raw String
```python

```

% - Format
