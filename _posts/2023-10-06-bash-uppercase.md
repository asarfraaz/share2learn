---
title: "Bash: Convert text to uppercase"
date: 2023-10-06
author: Sarfraaz Ahmed
category: TIL
---


We were writing a Bash Shell script where a word is taken as command line
argument. This word is then used a key to fetch the corresponding field from a
csv file. All worked fine, except that the student asked if we can give the
command line argument in lower case

That got us into thinking. The key in the csv file was all in uppercase. So, as
long as we gave the word on the command line argument in uppercase, we could
use it to match the line that contained the key using `awk`. But, if the
command line argument is provided in lower case ( just because it is more
easier for the user to type the input in lower case than in uppercase ), then
we need to convert it to uppercase, before looking it up in the csv file

One way that I knew of converting the word to uppercase is using `tr` command like this:

```bash
shell$ name="Ajay"
shell$ echo $name
Ajay
shell$ 
shell$ echo $name | tr 'a-z' 'A-Z'
shell$ echo $name
AJAY
shell$
```

## Bash Parameter Expansion

This task becomes pretty easy when we use "Parameter Expansion" feature of
Bash. This is how we can change all characters to upper case using "Parameter
Expansion" in Bash

```bash
shell$ name="Ajay"
shell$ echo $name
Ajay
shell$ 
shell$ echo ${name^^}
shell$ echo $name
AJAY
shell$
```

For more: Read "[Bash Shell Expansion Manual](https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)"


## Discussion

[Start a discussion on GitHub](https://github.com/asarfraaz/share2learn/discussions/new/choose){:target="_blank"} about this article and let me know your thoughts or suggestions.

