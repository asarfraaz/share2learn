---
title: "String Formatting"
date: 2021-09-28
author: Arjun
category: Tutorial
---

<h2>Here is the list of complete set of symbols which can be used along with "%"</h2>

%c	character

%s	string conversion via str() prior to formatting
```python
>>> x = 'python'
>>> print("Hello %s , %s to SharetoLearn!" %(x,"Welcome"))
Hello python , Welcome to SharetoLearn!
```

%i	signed decimal integer

%d	signed decimal integer

%u	unsigned decimal integer

%o	octal integer

%x	hexadecimal integer (lowercase letters)

%X	hexadecimal integer (UPPERcase letters)

%e	exponential notation (with lowercase 'e')

%E	exponential notation (with UPPERcase 'E')

%f	floating point real number

%g	the shorter of %f and %e

%G	the shorter of %f and %E


<h2>Other supported symbols in Python</h2>

"*"	argument specifies width or precision
	
"-"	 left justification

"+"	display the sign

<sp>	leave a blank space before a positive number
  
"#"	add the octal leading zero ( '0' ) or hexadecimal leading '0x' or '0X', depending on whether 'x' or 'X' were used.
  
0	pad from left with zeros (instead of spaces)
  
"%"	'%%' leaves you with a single literal '%'
  
(var)	mapping variable (dictionary arguments)
  
m.n.	m is the minimum total width and n is the number of digits to display after the decimal point (if appl.)
  
