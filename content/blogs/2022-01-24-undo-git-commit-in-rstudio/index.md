---
title: Github with RStudio
subtitle: Tricks of trade I learnt along the way
summary: Tricks of trade I learnt along the way
author: Harshvardhan
date: '2022-01-24'
slug: github-rstudio
categories:
  - R
tags:
  - R
---

## Starting a Project or Password Conflicts

If you are starting a project, jump to this. If you had a project that used password for commits (discontinued today, Aug 13 2021), jump to the first article. If it still does not resolve your issues, try the next three in that order.

-   [Simplest Guide on Github with R](https://gist.github.com/Z3tt/3dab3535007acf108391649766409421) This literally solves more than 80 per cent of my problems.

## Undo git commit in RStudio for more than 100 mb files

Every once in a while, you will end up trying to upload something in your local files that you do not want to commit to Github repository. How do you release that commit from R Studio? Github has a hard limit of 100 mb per file and I occasionally fail trying to upload it. Analysis paralysis.

![](images/Screen%20Shot%202022-01-24%20at%205.55.28%20PM.png "Error message on uploading file with size larger than 100 mb.")

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

## Some additional resources

-   <https://rfortherestofus.com/2021/02/how-to-use-git-github-with-r/>

-   <https://happygitwithr.com/credential-caching.html#credential-caching>

-   <https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/>
