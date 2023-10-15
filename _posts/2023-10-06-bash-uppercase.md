---
title: "Bash: Convert text to uppercase"
date: 2023-10-06
author: Sarfraaz Ahmed
category: TIL
---


We were writing a Bash Shell script where a word is taken as command line
argument. This word is then used as key to fetch a line from a csv file and
then pull out some specific field in it using `awk` command. All worked fine,
except that the student asked if we can give the command line argument in lower
case

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

The `tr` command maps every single lowercase alphabet `'a-z'` with its
corresponding uppercase alphabet `'A-Z'`

The problem with this approach is that everytime we use a pipe (`|`), a new
shell is launched to execute the command. So, in this case, there are 2 shell
processes created. One shell process is created for `echo` and it's output is
then piped to another shell process that is created for `tr`. It would be more
efficient if the entire string operation is performed in a single shell process

## Bash Parameter Expansion

This  efficiency can be achieved using "Parameter Expansion" feature of Bash.
The code for this task also becomes pretty easy. We can use `^^` to change all
characters to upper case inside "Parameter Expansion" in Bash as shown below


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

If we had to do the opposite and change all characters to lowercase, then we
could use `,,` inside Parameter Expansion in Bash as shown below


```bash
shell$ name="Ajay"
shell$ echo $name
Ajay
shell$ 
shell$ echo ${name,,}
shell$ echo $name
ajay
shell$ 
```

For more: Read "[Bash Shell Expansion Manual](https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html){:target="_blank"}"


## Discussion

[Start a discussion on GitHub](https://github.com/asarfraaz/share2learn/discussions/new/choose){:target="_blank"} about this article and let me know your thoughts or suggestions.

