---
layout: default
title: Pull Requests & Reviews
description: Principles for developers (maintainers and contributors)
---

> disclaimer: If I've asked you to read this, I'm trying to say SORRY. I am not defending myself. I am simply explaining how I made a mistake.
> I am not a bad programmer. I am a human with a work-in-progress laziness issue.

Pull requests (PRs) are great.

- As a contributor, you can implement a new feature or bug-fix and have your contribution merged upstream with visible accreditation.
- As a maintainer, it means some very intelligent, enthusiastic user has found an issue; invested time to debug and investigate your code; come up with a way to fix the issue; implemented said method; looked into your contributing guidelines, and followed said instructions to run tests, debug and fix their contribution, and (finally!) open a PR. That's a lot of effort.

But there's a hitch: maintainers are going to be much more familiar with the codebase. They follow some project design conventions. These are things which no contributor can be expected to bother themselves with -- they've already put in so much effort!

The natural tendency is for maintainers to fix these more pragmatic discrepancies before merging (by rewriting or reimplementing large parts of a PR), seemingly ignoring or belittling the massive amount of effort contributors have put in.

The new tendency (thanks to many other articles and blog posts on this topic) has been to merge imperfect PRs to avoid causing offence.

**THIS IS WRONG.**

Deep breath. It sounds bad to dispute recommendations claiming to "reduce offence." My point, however, is that they are not the most effective way of reducing potential for offence, and instead introduce additional problems.

If maintainers merge "imperfect" PRs, they will often later (post-merge) quietly fix the issues. This is bad for a couple of reasons:

- the contributor may no longer be given credit for their ideas (e.g. if all their surviving lines of code are changed), and
- the refactoring may not be actually required, consistent, or "correct." At worst, it may even introduce a bug.

Alternatively, post-merge, the issues may be forgotten and never addressed. Eventually, this could culminate in an unmaintainable mess, or at the very least increase the amount of effort needed to understand and debug the codebase.

If instead these "pedantic/polishing/finessing" changes were made in the original PR, the maintainer and contributor can review each other's code.

Worried about causing offence? There's a simple solution to that: communicate. It's a thing that programmers have been told they're not good at.

**THIS IS WRONG.**

Programmers are humans. All humans are better at communicating with other humans than with computers.

Note that opening a follow-up ticket (issue or PR) clearly linking to the original one with the relevant contributor clearly mentioned/contacted is exactly the same as doing everything in the original PR (in terms of causing offence without appropriate communication) but potentially better programming practice (in terms of subdividing problems).

Personally, I've never knowingly merged an imperfect PR (without opening an immediate follow-up ticket).
However, I have -- on occasion -- failed to communicate appropriately.
That's because I was being a lazy human. I was not being a bad programmer.

If you have to choose between accidentally causing occasional offence versus accidentally causing occasional build up of technical debt; it's better to risk accidental offence. It takes less time to rectify. Saying "sorry" is much quicker and safer to do than refactoring. The wider user base will appreciate the resultant clean, consistent code. The contributor (who by definition has already demonstrated a high level of intelligence and enthusiasm) is far more likely to accept your apologies instead of morphing into a troll.
