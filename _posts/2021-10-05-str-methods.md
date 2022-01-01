---
title: "String Methods"
date: 2021-10-05
author: Arjun
category: Tutorial
---

## List of String Methods mentioned in this post

1. [capitalize()](#capitalize)
1. [casefold()](#casefold)
2. [center()](#center)
3. [count()](#count)
4. [encode()](#encode)
5. [endswith()](#endswith)
6. [expandtabs()](#expandtabs)
7. [find()](#find)
8. [format()](#format)
9. [format_map()](#format_map)
10. [index()](#index)

---

<div id="capitalize"/>

**capitalize()**	Converts the first character of the string to a capital (uppercase) letter
```python
>>> string = "welcome to share to learn"
>>> string.capitalize()
'Welcome to share to learn'
>>>
```

<div id="casefold"/>

**casefold()**	Implements caseless string matching
```python
>>> string = "welcome to SHARE TO LEARN"
>>> string.casefold()
'welcome to share to learn'
```

<div id="center"/>

**center()**	Pad the string with the specified character.
```python
>>> str.center(12,"-")
'---Python---'
>>>
```

<div id="count"/>

**count()**	Returns the number of occurrences of a substring in the string.
```python
>>> string = "welcome to share to learn"
>>>
>>>
>>> string.count("we")
1
>>> string.count("to")
2
>>> string.count("l")
2
>>>
```

<div id="encode"/>

**encode()**	Encodes strings with the specified encoded scheme
```python
>>> string
'welcome to share to learn'
>>> string.encode()
b'welcome to share to learn'
>>>
>>> string.encode("ascii","ignore")
b'welcome to share to learn'
>>>
>>> string.encode("ascii","replace")
b'welcome to share to learn'
>>>
```

<div id="endswith"/>

**endswith()**	Returns “True” if a string ends with the given suffix
```python
>>> string
'welcome to share to learn'
>>>
>>> string.endswith("n")
True
>>>
>>>
>>> string.endswith("l")
False
>>> string.endswith("to")
False
>>> string.endswith("learn")
True
>>>
```

<div id="expandtabs"/>

**expandtabs()**	Specifies the amount of space to be substituted with the “\t” symbol in the string
```python
>>> sentence = "10\t20\t30"
>>> sentence
'10\t20\t30'
>>> print(sentence)
10	20	30
>>> print(sentence.expandtabs(tabsize=15))
10             20             30
>>> sentence.expandtabs(tabsize=15)
'10             20             30'
```

<div id="find"/>

**find()**	Returns the lowest index of the substring if it is found
```python
>>> string = "welcome to share to learn"
>>> string.find("share")
11
>>> string.find("to")
8
```

<div id="format"/>

**format()**	Formats the string for printing it to console
```python
>>> print("Welcome to {} to {}".format("Share","Learn"))
Welcome to Share to Learn
>>> print("Welcome to {0} to {1}".format("Share","Learn"))
Welcome to Share to Learn
>>> print("Welcome to {1} to {0}".format("Share","Learn"))
Welcome to Learn to Share
```

<div id="format_map"/>

**format_map()**	Formats specified values in a string using a dictionary
```python
>>> lunch = {
            "Food": "Pizza", 
            "Drink": "Juice"}
>>> print("Lunch: {Food}, {Drink}".format_map(lunch))
Lunch: Pizza, Juice
>>> class Default(dict):
        def __missing__(self, key):
            return key
>>> lunch = {"Drink": "Juice"}
>>> print("Lunch: {Food},{Drink}".format_map(Default(lunch)))
Lunch: Food, Juice
```

<div id="index"/>

**index()**	Returns the position of the first occurrence of a substring in a string
```python
>>> string
'welcome to share to learn'
>>> string.index("to")
8
>>>
>>> string.index("t")
8
>>> string.index("o")
4
>>> string.index("learn")
20
>>>
```

**isalnum()**	Checks whether all the characters in a given string is alphanumeric or not
```python
>>> string
'welcome to share to learn'
>>> string.isalnum()
False
>>> sentence = "HelloPython123"
>>> sentence.isalnum()
True
>>> sentence1 = " $ ***!"
>>> sentence1.isalnum()
False
>>>
```

**isalpha()**	Returns “True” if all characters in the string are alphabets
```python
>>> sentence
'HelloPython123'
>>> sentence.isalpha()
False
>>> sentence1
'welcome to share to learn'
>>> sentence1.isalpha()
False
>>> sentence = "HelloPython"
>>> sentence.isalpha()
True
>>>
```

**isdecimal()**	Returns true if all characters in a string are decimal
```python
>>> string
'Welcome to Share to learn'
>>> string.isdecimal()
False
>>> string1 = "500"
>>> string1.isdecimal()
True
>>>
```

**isdigit()**	Returns “True” if all characters in the string are digits
```python
>>> string1 = "500"
>>> string1.isdigit()
True
>>> string2 = "500.1"
>>> string2.isdigit()
False
>>>
```

**isidentifier()**	Check whether a string is a valid identifier or not
```python
>>> string1
'500'
>>> string1.isidentifier()
False
>>> string2 = "user1"
>>> string2.isidentifier()
True
>>>
```

**islower()**	Checks if all characters in the string are lowercase
```python
>>> string
'Welcome to Share to learn'
>>> string.islower()
False
>>> string1 = "welcome to share to learn"
>>> string1.islower()
True
>>>
```

**isnumeric()**	Returns “True” if all characters in the string are numeric characters
```python
>>> string
'Welcome to Share to learn'
>>> string.isnumeric()
False
>>> string1 = "123456"
>>> string1.isnumeric()
True
>>>
```

**isprintable()**	Returns “True” if all characters in the string are printable or the string is empty
```python
>>> string
'Welcome to Share to learn'
>>> string.isprintable()
True
>>> string1
'500'
>>> string1.isprintable()
True
>>> string2
'\t'
>>> string2.isprintable()
False
>>>
```

**isspace()**	Returns “True” if all characters in the string are whitespace characters
```python
>>> string
'Welcome to Share to learn'
>>> string.isspace()
False
>>> sentence = "\t"
>>> sentence.isspace()
True
>>>
```

**istitle()**	Returns “True” if the string is a title cased string
```python
>>> string
'Welcome to Share to learn'
>>> string.istitle()
False
>>> string1
'500'
>>> string1.istitle()
False
>>> sentence
'\t'
>>> sentence.istitle()
False
>>> sentence1 = "Python"
>>> sentence1.istitle()
True
>>>
```

**isupper()**	Checks if all characters in the string are uppercase
```python
>>> string
'Welcome to Share to learn'
>>> string.isupper()
False
>>> sentence = "HELLO THERE"
>>> sentence.isupper()
True
>>>
```

**join()**	Returns a concatenated String
```python
>>> a = "-"
>>> print(a.join("123"))
1-2-3
>>>
>>> a = "##"
>>> print(a.join("HELLO"))
H##E##L##L##O
>>>
```

**ljust()**	Left aligns the string according to the width specified
```python
>>> sentence = "Python"
>>> a = sentence.ljust(12, "-")
>>> print(a)
Python------
>>>
```

**lower()**	Converts all uppercase characters in a string into lowercase
```python
>>> sentence
'Welcome to Share to learn'
>>> sentence.lower()
'welcome to share to learn'
>>> sentence1
'HELLO THERE'
>>> sentence1.lower()
'hello there'
>>>
```

**lstrip()**	Returns the string with leading characters removed
```python
>>> sentence
'   Python  '
>>> sentence.lstrip()
'Python  '
>>>
```

**maketrans()**	 Returns a translation table
```python

```

**partition()**	Splits the string at the first occurrence of the separator 
```python
>>> data
'Welcome-to-sharetolearn'
>>> data.partition("-")
('Welcome', '-', 'to-sharetolearn')
>>>
```

**replace()**	Replaces all occurrences of a substring with another substring
```python
>>> data
'Hello Python'
>>> data.replace("Hello","Bye")
'Bye Python'
>>>
```

**rfind()**	Returns the highest index of the substring
```python
>>> sentence
'Hello-Python'
>>> sentence.rfind("P")
6
>>>
```

**rindex()**	Returns the highest index of the substring inside the string
```python
>>> string
'Welcome to Share to learn'
>>> string.rindex("S")
11
>>> string.rindex("l")
20
>>>
```

**rjust()**	Right aligns the string according to the width specified
```python
>>> sentence = "Hello Python"
>>> sentence1 = mystr.rjust(20,
"-")
>>> print(sentence1)
--------Hello Python
```

**rpartition()**	Split the given string into three parts
```python
>>> sentence = "Hello Python"
>>>
print(sentence.rpartition("."))
('', '', 'Hello Python')
>>> print(sentence.rpartition(" "))
('Hello', ' ', 'Python')
```

**rsplit()**	Split the string from the right by the specified separator
```python
>>> sentence = "Hello Python"
>>> print(sentence.rsplit())
['Hello', 'Python']
>>> sentence = "Hello-Python-Hello"
>>>
print(sentence.rsplit(sep="-", maxsplit=1))
['Hello-Python', 'Hello']
```

**rstrip()**	Removes trailing characters
```python
>>> sentence
'   Python  '
>>> sentence.rstrip()
'   Python'
>>>
>>> win_msg = "** We Won!!! **"
>>> win_msg
'** We Won!!! **'
>>> sentence.rstrip('*')
' We Won!!! '
>>>
```

**splitlines()**	Split the lines at line boundaries
```python
>>> sentence = '''
    Welcome to Share to Learn
    Happy Learning
'''
>>> sentence
'\nWelcome to Share to Learn\nHappy Learning\n'
>>> sentence.splitlines()
['', 'Welcome to Share to Learn', 'Happy Learning']
>>>
```

**startswith()**	Returns “True” if a string starts with the given prefix
```python
>>> sentence = "Welcome to Share to Learn"
>>> sentence.startswith("W")
True
>>> sentence.startswith("w")
False
>>> sentence.startswith("s")
False
>>>
```

**strip()**	Returns the string with both leading and trailing characters
```python
>>> sentence = "  Welcome to Share to Learn  "
>>> sentence.strip()
'Welcome to Share to Learn'
>>>
```

**swapcase()**	Converts all uppercase characters to lowercase and vice versa
```python
>>> sentence = "Welcome to Share to Learn"
>>> sentence.swapcase()
'wELCOME TO sHARE TO lEARN'
```

**title()**	Convert string to title case
```python
>>> sentence = 'WELCOME TO SHARE TO LEARN'
>>> sentence.title()
'Welcome To Share To Learn'

>>> sentence = 'welcome to share to learn'
>>> sentence.title()
'Welcome To Share To Learn'

>>> sentence = 'wELCOME TO sHARE TO lEARN'
>>> sentence.title()
'Welcome To Share To Learn'
```

**translate()**	Modify string according to given translation mappings
```python
>>> frm = "helloPython"
>>> to = "40250666333"
>>> trans_table =
str.maketrans(frm, to)
>>> secret_code = "Secret Code".translate(trans_table)
>>> print(secret_code)
S0cr06 C3d0
```

**upper()**	Converts all lowercase characters in a string into uppercase
```python
>>> sentence = "welcome to python"
>>> sentence.upper()
'WELCOME TO PYTHON'
```

**zfill()**	Returns a copy of the string with ‘0’ characters padded to the left side of the string
```python
>>> sentence = "1234"
>>> sentence.zfill(5)
'01234'
>>> sentence.zfill(9)
'000001234'
>>>
```
