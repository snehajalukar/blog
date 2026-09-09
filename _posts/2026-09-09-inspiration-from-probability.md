---
layout: post
title: The Math That Kept Me Applying
categories:
- General
feature_image: "https://picsum.photos/2560/600?image=872"
---

I got laid off in 2024, and job searching was rough. This math kept me going.

One of the things that weirdly kept me motivated was...literally math and probability. It's a weird time in the industry right now, and I have multiple friends that are job searching, so I figured I would type this up. And note: this probability math can apply to anything you want to try, not just job searching.

Here's the math:

Say, just for the sake of a pessimistic example, that every job application has a **1% chance** of turning into a job.

A 1% chance sounds terrible. Why even bother?

But that's the probability of **one** attempt.

If:

* `p` = the probability of getting hired from one application
* `n` = the number of applications

then the probability of getting **at least one yes** is:

![Probability of getting at least one yes, where p is the probability of getting hired from one application and n is the number of applications.](/assets/job-search-probability-formula.png)

For our example, `p = 0.01`, so:

`1 - (1 - 0.01)^n`

or:

`1 - (0.99)^n`

And this is where it gets interesting.

![Probability examples for 2, 10, 100, and 500 applications assuming a 1% chance per application.](/assets/job-search-probability-examples.png)

With **2 attempts**, you're at about **1.99%**.

With **10**, **9.56%**.

With **100**, **63.40%**.

With **500**, **99.34%**.

Again, hiring does not actually work like a perfectly controlled probability experiment. Every application is different. Your resume improves. Your interviewing improves. Referrals change the odds. Some jobs are a much better fit than others. Economic conditions change. And no number of applications can mathematically guarantee you a job.