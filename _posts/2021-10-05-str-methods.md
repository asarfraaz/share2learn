---
title: "String Methods"
date: 2021-10-05
author: Arjun
category: Tutorial
---

**capitalize()**	Converts the first character of the string to a capital (uppercase) letter
```python
>>> string = "welcome to share to learn"
>>> string.capitalize()
'Welcome to share to learn'
>>>
```

**casefold()**	Implements caseless string matching
```python
>>> string = "welcome to SHARE TO LEARN"
>>> string.casefold()
'welcome to share to learn'
```

**center()**	Pad the string with the specified character.
```python
>>> str.center(12,"-")
'---Python---'
>>>
```

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

**expandtabs()**	Specifies the amount of space to be substituted with the “\t” symbol in the string
```python
>>> str = "10\t20\t30"
>>> str
'10\t20\t30'
>>> print(str)
10	20	30
>>> print(str.expandtabs(tabsize=15))
10             20             30
>>> str.expandtabs(tabsize=15)
'10             20             30'
```

**find()**	Returns the lowest index of the substring if it is found
```python
>>> string = "welcome to share to learn"
>>> string.find("share")
11
>>> string.find("to")
8
```

**format()**	Formats the string for printing it to console
```python
>>> print("Welcome to {} to {}".format("Share","Learn"))
Welcome to Share to Learn
>>> print("Welcome to {0} to {1}".format("Share","Learn"))
Welcome to Share to Learn
>>> print("Welcome to {1} to {0}".format("Share","Learn"))
Welcome to Learn to Share
```

**format_map()**	Formats specified values in a string using a dictionary

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
>>> str = "HelloPython123"
>>> str.isalnum()
True
>>> str1 = " $ ***!"
>>> str1.isalnum()
False
>>>
```

**isalpha()**	Returns “True” if all characters in the string are alphabets
```python
>>> str
'HelloPython123'
>>> str.isalpha()
False
>>> string
'welcome to share to learn'
>>> string.isalpha()
False
>>> str = "HelloPython"
>>> str.isalpha()
True
>>>
```

**isdecimal()**	Returns true if all characters in a string are decimal

**isdigit()**	Returns “True” if all characters in the string are digits

**isidentifier()**	Check whether a string is a valid identifier or not

**islower()**	Checks if all characters in the string are lowercase

**isnumeric()**	Returns “True” if all characters in the string are numeric characters

**isprintable()**	Returns “True” if all characters in the string are printable or the string is empty

**isspace()**	Returns “True” if all characters in the string are whitespace characters

**istitle()**	Returns “True” if the string is a title cased string

**isupper()**	Checks if all characters in the string are uppercase

**join()**	Returns a concatenated String

**ljust()**	Left aligns the string according to the width specified

**lower()**	Converts all uppercase characters in a string into lowercase

**lstrip()**	Returns the string with leading characters removed

**maketrans()**	 Returns a translation table

**partition()**	Splits the string at the first occurrence of the separator 

**replace()**	Replaces all occurrences of a substring with another substring

**rfind()**	Returns the highest index of the substring

**rindex()**	Returns the highest index of the substring inside the string

**rjust()**	Right aligns the string according to the width specified

**rpartition()**	Split the given string into three parts

**rsplit()**	Split the string from the right by the specified separator

**rstrip()**	Removes trailing characters

**splitlines()**	Split the lines at line boundaries

**startswith()**	Returns “True” if a string starts with the given prefix

**strip()**	Returns the string with both leading and trailing characters

**swapcase()**	Converts all uppercase characters to lowercase and vice versa

**title()**	Convert string to title case

**translate()**	Modify string according to given translation mappings

**upper()**	Converts all lowercase characters in a string into uppercase

**zfill()**	Returns a copy of the string with ‘0’ characters padded to the left side of the string
