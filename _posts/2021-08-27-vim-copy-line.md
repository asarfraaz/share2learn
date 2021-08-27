---
title: "Duplicating a line in Vi"
date: 2021-08-27
author: Sarfraaz Ahmed
category: TIL
---

Today I Learnt that, you can use

```vim
:t.
```

to duplicate the line on which your cursor is present

## Use case

Usually, when working with existing code [ _to either trace through the code, or debug it_ ]
I would use the following keys to duplicate the current line on which my cursor is present

```vim
yyp
```

But now, with ```vim :t. ```, its much easier

## Helpful Tip

Recently, I was updating my log book where each line refers to works done on each day

Every day, a new entry gets added at the end of file.

While adding the data for today, I noticed that the data that I needed was already present in a line written 5 lines above the last line of the file

So, I moved the cursor to the existing line and typed

```vim
:t$
```

To duplicate the present line to the end of the file.
