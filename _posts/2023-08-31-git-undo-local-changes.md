---
title: "Undo local changes in a Git Repository"
date: 2023-08-31
author: Sarfraaz Ahmed
category: TIL
---

I cloned a Git Repository and started doing some changes. After working for sometime, I realised that the solution I was trying would never work. I wanted to try another approach.

To do this, I wanted to first undo the changes I had with the bad solution. So that I can then start afresh from the proper base code

The steps I followed were as below :

## Cloning Git Repository

To clone the Git Repository

```bash
bash:[work]$ git clone https://github.com/asarfraaz/share2learn
bash:[work]$ ls
share2learn
bash:[work]$ cd share2learn
bash:[share2learn]$ 
```

## Find modified files in Git Repository

To find out the files that were modified

```bash
bash:[share2learn]$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   some_folder/somefile.txt

no changes added to commit (use "git add" and/or "git commit -a")
bash:[share2learn]$ git diff
# Displays all the differences since the last commit
.....
bash:[share2learn]$ ls
```

*NOTE:* The changes made were present in working directory and were *not* yet added to the staging area

I wanted to undo these changes some in 'somefile.txt'

## Undo changes in working tree of Git Repository

To revert the repository to the state it was prior to my changes

```bash
bash:[share2learn]$ git restore somefolder/somefile.txt
bash:[share2learn]$ git status
On branch main
nothing to commit, working tree clean
bash:[share2learn]$
```

Another way to do the same is using `git checkout -p`. You can read more about it in this [stackoverflow answer](https://stackoverflow.com/a/76160411/4106458)

## Discussion

[Start a discussion on GitHub](https://github.com/asarfraaz/share2learn/discussions/new/choose){:target="_blank"} about this article and let me know your thoughts or suggestions.


