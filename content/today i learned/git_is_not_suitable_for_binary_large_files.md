---
title: "TIL: Git is not suitable for binary large files"
date: 2022-03-27T02:02:06-03:00
draft: false
tags: ["git"]
---

I’d never thought about that until faced this problem. For me, git was the best option to keep track of file differences, either a text file or a binary file.

##### The Problem
Today I'm facing a problem: I've tried to add PSD files to a git repository.
That's is not "wrong" but is a big mistake. If the PSD files are changed often you will end up with a large git repository. With it, every time someone tries to pull your updates in a PSD file they have to download the entire file.

##### Example
Suppose that you have a PSD file that is 200MB large. With 3 changes you will have a repository that is 600MB large :0. This is because git cannot make delta from binary files.


Git uses [Delta Encoding](https://en.wikipedia.org/wiki/Delta_encoding).  With makes, a commit doesn't store all the files that were changed. Instead, they store the patch of the changes. With PSD files or any other binary files, git cannot make a patch, because every change in a binary file also changes all file structures. (In truth git can make a patch but the size of the patch is the same of the original file)

##### Conclusion
Git has a plugin named **git-lfs** to help in cases like this. Again git help but not resolve. Git was not made for this use case. No code version system was made for this. Try to use shared storage and make sure that no one is editing the same files at a time.