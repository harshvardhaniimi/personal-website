---
title: Script monkey! 🐒
subtitle: Recently, I learnt a neat trick during my internship at HP.
summary: "Use a Script Monkey in your codebase at all locations where you need to change things manually. All that involves is writing an extra comment saying 'Script Monkey'. Later on, search for all monkeys in the script and make the changes. Simple."
author: Harshvardhan
date: '2022-08-01'
slug: script-monkey
categories:
  - R
  - coding
  - Python
tags: []
---

Recently, I learned a neat trick during my internship at HP.

Sometimes you only need a few changes in the existing script before rerunning it all. For example, while working on a periodically executed project, we needed to run the same set of Jupiter notebooks every month. The code didn't change, barring a few parameters.

Usually, I recommend keeping the parameters at the beginning, so you notice what you need to change readily. But sometimes, you cannot avoid changes midway through the script.

How do you identify all the changes you need manually before hitting "restart kernel and run all" (in Jupyter Notebooks) or "Source" (in RStudio)?

# Hi Monkey 🐵

Use a Script Monkey in your codebase at all locations where you need to change things manually. All that involves is writing an additional comment saying "Script Monkey". Later, search for all monkeys in the script and make the changes. Simple.


```python
# Script monkey: Add current month and lag
df = pd.DataFrame(month = ['2022-02', '2022-03', '2022-03'], 
                  lag = [1, 2, 3])
```

Adding a small comment with #Script Monkey will save you hours looking through the codes. Just Cmd + F (⌘ + F in Mac or Ctrl + F in Windows) for "monkey", and you will know what to keep track of!

# Beyond Scripts

Scripts are only the beginning. Later on, you might need to modify more things. In that case, use Data Monkey, Tuning Monkey, Timing Monkey -- and more!

[Monkey will find its way to you.](https://www.instagram.com/reel/CO8WNMDnjLnKt9Pscy4_74xykrDqwZXAtrG2zw0/)[^1]

[^1]: Featured image credit: <a href='https://www.freepik.com/vectors/cute-monkey'>Cute monkey vector created by catalyststuff - www.freepik.com</a>