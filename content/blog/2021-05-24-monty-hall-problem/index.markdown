---
title: Monty Hall Problem
subtitle: Would you change your original choice with new information?
summary: Would you change your original choice with new information?
author: Harshvardhan
date: '2021-05-24'
slug: []
categories:
  - statistics
tags:
  - statistics
  - probability
  - confusing
---

I first heard of Monty Hall problem around four years ago. In class, a professor showed us how we weren't willing to change our decisions even after suggestive evidence showed us otherwise. What's Monty Hall problem, you ask?

Monty Hall problem is a brain teaser based on probability, inspired by the show Let's Make a Deal. The problem goes like this:

> Suppose you're on a game show, and you're given the choice of three doors: Behind one door is a car; behind the others, goats. You pick a door, say No. 1, and the host, who knows what's behind the doors, opens another door, say No. 3, which has a goat. He then says to you, "Do you want to pick door No. 2?" Is it to your advantage to switch your choice?

## Think your answer before reading further.

The problem has multiple solutions, from very simple to complex Bayesian simulations. In this short note, I will only talk about the most straightforward solution using the principle of indifference. The principle of indifference says that if you have no extra information, you should be indifferent between your choices. If you have a coin and you don't know the probability of getting a head, the best starting point is 50 per cent. If you haven't studied for the exam and have an objective exam, all options are equally likely to be correct.

Sounds simple, but this is easily misinterpreted and prone to errors. Remind yourself to be extra careful when using this.

For our Monty Hall, let us say you don't know anything about your choices. You are equally likely to choose any one --- 1/3 probability. Say you chose the first one, and Mr Hall removes the second option. What is the likelihood that you are still correct and the car is actually behind the first door? Now that there are only two doors left, it should be 1/2. You should be indifferent between the two doors. Wrong. What you do not account for is that this probability does not account for the additional information that Mr Hall removed the second option. Did you consider conditional probability? This reminds me of Chekhov's Gun --- a movie-making principle that says every element in the story must be necessary or it shouldn't be there. Why did Mr Hall remove the option? It should have value.

Once you consider that additional information, think again of the problem. Mr Hall removes the second door from the game; the probabilities are recalculated. You initially chose the second door, and that door's chance remains fixed --- 1/3. You are right now if and only if you were right originally. But the third door's chance increases to 2/3. After all, the total probability should add up to one. Because that is the case, you should change your choice and quickly switch to door three.

If you switch your choice, you have around 66 per cent probability of taking that sedan home. If you didn't, well, only 33 per cent. Puzzled? I couldn't get it either. (It is a veridical problem; the correct answer is so counterintuitive that it seems absurd.)

As I said, there are [mathematical](https://www.khanacademy.org/math/precalculus/x9e81a4f98389efdf:prob-comb/x9e81a4f98389efdf:dependent-events-precalc/v/monty-hall-problem) and [simulation](http://www.math.ucsd.edu/~crypto/Monty/monty.html) proofs as well.

But why didn't you switch? Or why didn't I switch? Was it because I was taught to be disciplined and stick with a choice once I made it? Was it because I had invested in my first choice and didn't want to lose it? Or was it because I was afraid to take the risk?

My psychology professor had taught me about errors of omission vs errors of commission effect. People tend to stay inactive and lose rather than be active and take risks. Then there is endowment effect from development economics. Once we own a good, we start valuing it more than we had invested for it. We develop an attachment to it and an emotional bias for our decisions. It could have been that.

Or, maybe I was too lazy to switch.
