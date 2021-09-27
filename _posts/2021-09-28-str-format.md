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
```python
>>> print("%d" % 100)
100
>>> print("%d" % 0b1111)
15
>>> print("%03d" % 1)
001
>>> print("%03d" % 100.111)
100
>>> print("%03d" % 10.111)
010
```

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
```python
>>> x = 1.23456789
>>> print '%e | %f | %g' % (x, x, x)
1.234568e+00 | 1.234568 | 1.23457
```

**%G**	the shorter of %f and %E
```python
>>> x = 1.23456789
>>> print '%E | %f | %G' % (x, x, x)
1.234568E+00 | 1.234568 | 1.23457
```

