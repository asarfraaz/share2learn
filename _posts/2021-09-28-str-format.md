---
title: "String Formatting"
date: 2021-09-28
author: Arjun
category: Tutorial
---

<h2>Here is the list of complete set of symbols which can be used along with "%"</h2>

**%c** character
```python
>>> print ("%c" %'h')
h
>>> print ("%c" %104)
h
>>> print ("%c" %'"')
"
>>> print ("%c" %34)
"
```

**%s**	string conversion via str() prior to formatting
```python
>>> x = 'python'
>>> print("Hello %s , %s to SharetoLearn!" %(x,"Welcome"))
Hello python , Welcome to SharetoLearn!
```

**%i**	signed decimal integer
```python
>>> print("Hello %i + %i = %i" %(5,5,10))
Hello 5 + 5 = 10
```

**%d**	signed decimal integer

**%u**	unsigned decimal integer
```python
>>> u'Hello\u0020Python ! '
u'Hello Python ! '
```

**%o**	octal integer
```python
>>> print "%o" % 012
12
>>> print "%o" % 10
12  # Because 012 ==12
```

**%x**	hexadecimal integer (lowercase letters)
```python
>>> print ("%x" % 10)
a
>>> print ("%x" % 11)
b
>>> print ("%x" % 12)
c
```

**%X**	hexadecimal integer (UPPERcase letters)
```python
>>> print ("%X" % 10)
A
>>> print ("%X" % 11)
B
>>> print ("%X" % 12)
C
```

**%e**	exponential notation (with lowercase 'e')
```python
>>> '%e' % 1234567890
'1.234568e+09'
```

**%E**	exponential notation (with UPPERcase 'E')
```python
>>> '%E' % 1234567890
'1.234568E+09'
```

**%f**	floating point real number
```python
>>> print("Hello %f + %f = %f" %(5.1,5,10))
Hello 5.100000 + 5.000000 = 10.000000
```

**%g**	the shorter of %f and %e

**%G**	the shorter of %f and %E


<h2>Other supported symbols in Python</h2>

**"*"**	argument specifies width or precision
	
**"-"**	 left justification

**"+"**	display the sign

<sp>	leave a blank space before a positive number
  
**"#"**	add the octal leading zero ( '0' ) or hexadecimal leading '0x' or '0X', depending on whether 'x' or 'X' were used.
  
**0**	pad from left with zeros (instead of spaces)
  
"**%**"	'%%' leaves you with a single literal '%'
  
**(var)**	mapping variable (dictionary arguments)
  
**m.n.**	m is the minimum total width and n is the number of digits to display after the decimal point (if appl.)
  
