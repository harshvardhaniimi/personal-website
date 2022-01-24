---
title: Undo git commit in RStudio
subtitle: How to "delete" large file commits from RStudio without sending them to Github
summary: How to "delete" large file commits from RStudio without sending them to Github
author: Harshvardhan
date: '2022-01-24'
slug: undo-git-commit-in-rstudio
categories:
  - R
tags:
  - R
---

Every once in a while, you will end up trying to upload something in your local files that you do not want to commit to Github repository. How do you release that commit from R Studio?

Github has a hard limit of 100 mb per file and I occasionally fail trying to upload it. Analysis paralysis.

### TL;DR

1.  Ensure you only have commits that you want to delete in the Git pane. Then go to Git tab.
2.  Click on <i class="fas fa-cog"></i> (machine-like icon) and select "Shell...".
3.  In Shell, type: `git reset HEAD~`.
4.  Keep hitting the statement as many times as you have commits.
5.  Voila.

### Full Steps

First, ensure you have only the changes you do not want to commit. If I try commiting with `.key` file, it will fail as it's larger than 100 mb.

![](images/Screen%20Shot%202022-01-24%20at%205.45.58%20PM.png "Git Pane in RStudio")

I want to commit the last two changes (something about this blog post), so I will commit it and push changes to the [repository](https://github.com/harshvardhaniimi/personal-website). Then, I will go the <i class="fas fa-cog"></i> (machine-like icon) and click on "Shell...".

Now, I will paste in the Terminal window the magic spell: `git reset HEAD~`.
