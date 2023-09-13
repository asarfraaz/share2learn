---
title: "Use patch to Undo local Git Repository changes"
date: 2023-09-13
author: Sarfraaz Ahmed
category: TIL
---

Last week I learnt of [two ways to undo local changes in a Git Repository](https://asarfraaz.github.io/share2learn/til/2023/08/31/git-undo-local-changes.html){:target="_blank"}

This time, I thought of a slightly different scenario

## Scenario

Let's assume I have done some changes in my local Git Repository. And, then I realise that this change is good, except that it should be done after some other changes. So, I want to keep a copy of the current changes. That way, when I need to redo these changes, I can reuse the changes from the copy.

## Keeping a backup of the changes

To keep a backup of your changes before deleting them you can redirect the output of `git diff` command to a "patch" file. And later on when you need to reapply these changes you can use the very useful `patch` command to do it.

**NOTE:** This `patch` command is available only on Linux and Mac like machines, which I think are machines created to be used by developers.

Run the below command to create a "patch" file containing the changes of the required file

```bash
bash:[share2learn]$ git diff somefolder/somefile.txt > fix_abcd.patch
```

"fix_abcd.patch" file from the above command now contains all the changes of "somefile.txt" made in the local Git Repository.

## Remove local Git Repository changes

To remove the changes done in "somefile.txt" at the local Git Repository, reverse apply the patch using `-R` switch as shown below

```bash
bash:[share2learn]$ patch -R < fix_abcd.patch
```

**NOTE:** The above command does "input redirection" using `<` operator

Run the below command to verify that all local changes are removed

```bash
bash:[share2learn]$ git status somefolder/somefile.txt
...
nothing to commit, working tree clean
bash:[share2learn]$ 
```

## Applying the patch

Later on if you decide to reapply the changes to your local Git Repository. May be it is after you have committed some changes to either the same file or some other file. 

We can apply the changes from the "patch" file using `patch` command as below:

```bash
bash:[share2learn]$ patch somefolder/somefile.txt < fix_abcd.patch
```

**NOTE:** You may get some conflicts if "somefile.txt" contains any prior changes in the same lines are present in "fix_abcd.patch". You will have to manually fix the "conflicts" by choosing the lines of code you finally want to be present in your code

Do a `git diff` to verify if all changes that you wanted are present in the Repository


## Discussion

[Start a discussion on GitHub](https://github.com/asarfraaz/share2learn/discussions/new/choose){:target="_blank"} about this article and let me know your thoughts or suggestions.


