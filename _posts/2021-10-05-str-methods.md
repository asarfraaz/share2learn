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
```

**istitle()**	Returns “True” if the string is a title cased string
```python
```

**isupper()**	Checks if all characters in the string are uppercase
```python
```

**join()**	Returns a concatenated String
```python
```

**ljust()**	Left aligns the string according to the width specified
```python
```

**lower()**	Converts all uppercase characters in a string into lowercase
```python
```

**lstrip()**	Returns the string with leading characters removed
```python
```

**maketrans()**	 Returns a translation table
```python
```

**partition()**	Splits the string at the first occurrence of the separator 
```python
```

**replace()**	Replaces all occurrences of a substring with another substring
```python
```

**rfind()**	Returns the highest index of the substring
```python
```

**rindex()**	Returns the highest index of the substring inside the string
```python
```

**rjust()**	Right aligns the string according to the width specified
```python
```

**rpartition()**	Split the given string into three parts
```python
```

**rsplit()**	Split the string from the right by the specified separator
```python
```

**rstrip()**	Removes trailing characters
```python
```

**splitlines()**	Split the lines at line boundaries
```python
```

**startswith()**	Returns “True” if a string starts with the given prefix
```python
```

**strip()**	Returns the string with both leading and trailing characters
```python
```

**swapcase()**	Converts all uppercase characters to lowercase and vice versa
```python
```

**title()**	Convert string to title case
```python
```

**translate()**	Modify string according to given translation mappings
```python
```

**upper()**	Converts all lowercase characters in a string into uppercase
```python
```

**zfill()**	Returns a copy of the string with ‘0’ characters padded to the left side of the string
```python
```
