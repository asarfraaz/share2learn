---
title: "Adding sequential numbers to a file"
date: 2023-09-02
author: Sarfraaz Ahmed
category: TIL
---

## Using Vim is like magic !!!

I had a file with about 300 lines of rows. I wanted to number each row from 1 to the last number

This is a sample `csv` file that represents the file that I was working with.

```csv
Name,City
Abcd,Bangalore
Pqr,London
Xyz,Paris
...
Lmn,Tokyo
```

It has 2 columns, "Name" and "City". I wanted to insert a new column "Id" which numbers each row from 1 to the last number

## Setup the stage for the magic show

It took me less than a minute to number all the 300+ lines using Vim.

The steps I followed in Vim for doing this tedious task ( for 300 lines ) was as follows:

1. In the first row, add the text "Id," at the beginning the line
1. Move the cursor to the second line, first column
1. Number every row with value 1 using the below steps
    1. Create a new column using "Vertical visual block"
    2. Insert the number 1 for each row

```vim
Ctrl_vGI1,EscEsc
```

Explanation for the above command:
- **Ctrl_v** : _Vertical visual block start_
- **G** : _Take cursor to last line_
- **I** : _Take editor into Inert mode_
- **1,** : _Insert the characters 1 and ,_
- **EscEsc** : _Repeat the change ( insert 1 ) in all selected lines_

This resulted in the following new data

```csv
Id,Name,City
1,Abcd,Bangalore
1,Pqr,London
1,Xyz,Paris
...
1,Lmn,Tokyo
```

## Abracadabra

Now, for the magic:

- Move the cursor to the third line, first column ( the second line already contains the required number 1, so don't select it )
- To select the first column again either do

```vim
gv
```

or

```vim
Ctrl_vG
```

Then

```vim
gCtrl_a
```

This magically increments all the numbers sequentially resulting in the following

```csv
Id,Name,City
1,Abcd,Bangalore
2,Pqr,London
3,Xyz,Paris
...
328,Lmn,Tokyo
```

You would use the same keys irrespective of whether there were 300 or 300 million lines in the file !!!

<div align=center> 
** Using Vim is like magic !!! ** 
</div>

To learn more about this exciting Vim magic (like) command

```vim
:help v_g_CTRL-A
```

## Discussion

[Start a discussion on GitHub](https://github.com/asarfraaz/share2learn/discussions/new/choose){:target="_blank"} about this article and let me know your thoughts or suggestions.


