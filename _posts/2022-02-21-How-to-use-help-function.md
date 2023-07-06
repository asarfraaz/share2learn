---
title : How To Use Help In Python
date : 2022-02-22
author : Basavaraj
category : Tutorial
---

# help()

- We all  know what's the meaning of help. but we are not talking about that help word.

## What is Help in python?
    Basically help() is an function in the python. We have seen many kind of built in functions in the python
    those functions will perform some certain tasks. 
    But the help() function will actually gives the information about the particular object, string, class, variables, etc

  - How can we call the help() function?
  - There are two ways to call the function 
## 1. Calling function in the python cell just typing the keyword help().
  - It will give the information stored in the object in doc-string about the python and its objects.
  - Example:
  - First we will run the python then we will call the help() function.
 
  - ubuntu:~$ python3
  Python 3.8.10 (default, Nov 26 2021, 20:14:08) 
  [GCC 9.3.0] on linux
  Type "help", "copyright", "credits" or "license" for more information.

- Calling help() function in the python cell.

>>> help()

Welcome to Python 3.8's help utility!

If this is your first time using Python, you should definitely check out
the tutorial on the Internet at https://docs.python.org/3.8/tutorial/.

Enter the name of any module, keyword, or topic to get help on writing
Python programs and using Python modules.  To quit this help utility and
return to the interpreter, just type "quit".

To get a list of available modules, keywords, symbols, or topics, type
"modules", "keywords", "symbols", or "topics".  Each module also comes
with a one-line summary of what it does; to list the modules whose name
or summary contain a given string such as "spam", type "modules spam".

- Asking the question like what is object in the python in the cell.

help> object
- It will give content of the object.
class object
 |  The base class of the class hierarchy.
 |  
 |  When called, it accepts no arguments and returns a new featureless
 |  instance that has no instance attributes and cannot be given any.
 |  
 |  Built-in subclasses:
 |      async_generator
 |      BaseException
 |      builtin_function_or_method
 |      bytearray
 |      ... and 86 other subclasses
 |  
 |  Methods defined here:
 |  
 |  __delattr__(self, name, /)
 |      Implement delattr(self, name).
 |  
 |  __dir__(self, /)
 |      Default dir() implementation.
 |  
help>> class

help>> in ...... so on.

## 2. Way of writing help function is to help(object).
  - Here we are passing the particular question to help function then it will give the details about the particular object.
  - we can ask a question like this help(int) in any kind of editor.
 
- help(int)

- Help on class int in module builtins:
  class int(object)
 |  int([x]) -> integer
 |  int(x, base=10) -> integer
 |  
 |  Convert a number or string to an integer, or return 0 if no arguments
 |  are given.  If x is a number, return x.__int__().  For floating point
 |  numbers, this truncates towards zero.
 |  
 |  If x is not a number or if base is given, then x must be a string,
 |  bytes, or bytearray instance representing an integer literal in the
 |  given base.  The literal can be preceded by '+' or '-' and be surrounded
 |  by whitespace.  The base defaults to 10.  Valid bases are 0 and 2-36.
 |  Base 0 means to interpret the base from the string as an integer literal.
 |  >>> int('0b100', base=0)
 |  4
 |  
 |  Built-in subclasses:
 |      bool
 |  
 |  Methods defined here:

 -class int(object)
 |  int([x]) -> integer
 |  int(x, base=10) -> integer
 |  
 |  Convert a number or string to an integer, or return 0 if no arguments
 |  are given.  If x is a number, return x.__int__().  For floating point
 |  numbers, this truncates towards zero.
 |  
 |  If x is not a number or if base is given, then x must be a string,
 |  bytes, or bytearray instance representing an integer literal in the
 |  given base.  The literal can be preceded by '+' or '-' and be surrounded
 |  by whitespace.  The base defaults to 10.  Valid bases are 0 and 2-36.
 |  Base 0 means to interpret the base from the string as an integer literal.
 |  >>> int('0b100', base=0)
 |  4
 |  
 |  Built-in subclasses:
 |      bool
 |  
 |  Methods defined here:

- we can ask the questions for built in functions and also user defined functions classes objects etc.

- ****************************** end*********************************

